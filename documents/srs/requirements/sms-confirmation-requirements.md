# Enterprise SMS Notification & Communication Strategy

## 1. Overview
The TeaRoutePay system leverages automated SMS notifications to improve transparency and trust between the tea collection business and its external suppliers (farmers). 

Currently, farmers depend on manual receipts and verbal confirmations. The proposed automated SMS architecture will provide cryptographic-backed confirmations for daily collections and monthly financial disbursements via the integrated SMS Gateway (e.g., Dialog Enterprise SMS).

## 2. Objectives
* Provide immutable, digital proof of daily collection weights upon server synchronization.
* Provide instant notification of monthly vendor payout bank transfers.
* Eliminate physical receipt printing costs and reduce office inquiries.
* Enforce strict character limits to optimize gateway billing costs.

## 3. SMS Trigger Scenarios
The system shall orchestrate SMS notifications across two primary business domains:

| Scenario | Trigger Condition | Primary Purpose |
| :--- | :--- | :--- |
| **Daily Collection Sync** | Mobile offline payload successfully merges into the Central PostgreSQL database. | Confirm net weight and daily yield to the farmer. |
| **Monthly Payout Execution** | Desktop system updates a monthly batch record to the `COMPLETED` state. | Notify farmer of successful bank transfer/cash availability. |

## 4. Physical Deduction Logic (Pre-SMS Net Weight)
Before the Daily Collection SMS is generated, the system must calculate the exact Net Weight. Tea collectors evaluate physical sacks for "Rope" (heavy tying materials) and "Water" (wet leaves).

**Deduction Rules:**
* **Rope Sack:** 1.0 kg deducted per identified rope sack.
* **Water Content:** 1.0 kg deducted per identified wet sack.

**Mathematical Execution:**
`Final Net Weight = Gross Weighed Amount - (Rope Sacks × 1.0 kg) - (Wet Sacks × 1.0 kg)`
*The calculated `Final Net Weight` is the absolute value that must be transmitted in the SMS.*

## 5. Technical Constraints & Cost Optimization
To prevent excessive billing from the SMS Gateway API, the system must adhere to strict character encoding limits:

* **Language Support:** The system must support English (GSM-7 encoding) and Local Languages (Sinhala/Tamil via UCS-2 Unicode encoding).
* **Length Optimization:** * English payloads MUST be kept strictly under **160 characters** (1 SMS credit).
  * Unicode (Sinhala/Tamil) payloads MUST be kept strictly under **70 characters** (1 SMS credit).
* Variable interpolation (e.g., Farmer Names) must be dynamically truncated if they risk pushing the message length into a 2-credit billing tier.

## 6. Required SMS Payloads & Templates
The system will construct messages using dynamic templates.

### 6.1 Daily Collection Confirmation
* **Trigger:** Post-Sync
* **Data Variables:** `[Date]`, `[Net_Weight]`
* **English Example (Under 160 chars):**
  > TeaRoutePay: Your collection on 14-May was synced. Net Weight: 48.5kg. Thank you!

### 6.2 Monthly Payout Confirmation
* **Trigger:** Payment state changes to `COMPLETED`
* **Data Variables:** `[Month]`, `[Net_Amount]`, `[Bank_Name]`
* **English Example (Under 160 chars):**
  > TeaRoutePay: May payout of LKR 45,000 transferred to BOC. Arrears/Deductions applied. 

## 7. Delivery Failure & Retry Architecture
SMS delivery via cellular networks is inherently unreliable. The system shall not drop failed messages.
1. **Asynchronous Queue:** All SMS triggers are pushed to a background queue, preventing UI blocking for office staff.
2. **Automated Retry:** If the Gateway API returns a `5xx` error or delivery failure, the system will automatically attempt 3 retries using an exponential backoff strategy.
3. **Dead Letter Queue (DLQ):** After 3 failed attempts, the message is marked as `FAILED` and flagged on the Desktop UI dashboard for office staff to manually verify the farmer's registered phone number.
