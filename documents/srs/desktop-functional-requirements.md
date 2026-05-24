# Desktop Application Functional Requirements

## Overview
The TeaRoutePay desktop application is designed for office staff and business owners to securely manage tea collection accounting, token generation, payment handling, deductions, and reporting workflows. 

This document outlines the functional requirements for the office-side system, ensuring accurate monthly calculations, secure payment execution, distributed data synchronization, and reliable manual backup operations, meeting the criteria for issue [SENG31242-#12].

---

## 1. Major Desktop Application Features
The system supports the following core capabilities:

| Feature | Description |
| :--- | :--- |
| **User Authentication & Token Generation** | Secure access management using generated authentication tokens for sessions and synchronization. |
| **Collection Record Management** | Interface to view, verify, and input daily tea collection logs. |
| **Farmer Payout & Employee Payroll** | Automated calculation of monthly farmer vendor payouts and internal employee salaries. |
| **Payment Handling & Execution** | Comprehensive system for processing, recording, tracking, and notifying actual financial disbursements. |
| **Deduction & Advance Management** | System for tracking and applying loans, advances, fertilizer, and personal tea issue deductions. |
| **Receipt Generation** | Automated creation of digital and printable receipts with unique transaction tokens. |
| **Report Generation** | Compilation of financial, operational, and historical reports. |
| **Data Synchronization** | Token-secured synchronization with mobile collection devices featuring timestamp conflict resolution. |
| **Manual Backup Entry** | Provision for prioritized manual record entry during synchronization or device failures. |

---

## 2. Functional Requirements

### FR-01 – User Authentication & Token Generation
* **Input:** Username, Password.
* **Process:** Validates credentials and generates a secure session token (JWT). Generates API tokens for mobile synchronization.
* **Output:** Granted system access, session token, sync token.
* **Validation:** Credentials must match database records; tokens must expire automatically after a predefined period of inactivity.

### FR-02 – Collection Record Management
* **Input:** Synchronized mobile data, manual entries.
* **Process:** Processes and securely stores daily collection weights.
* **Output:** Updated central database.
* **Validation:** Distributed Idempotency—prevents duplicate collection entries for the exact same Farmer ID and Date using composite key constraints.

### FR-03 – Monthly Farmer Payment Calculation
* **Input:** Total approved collection weight, current tea rates, aggregated deductions, advance payments.
* **Process:** Computes gross tea value, subtracts loans, advances, and other deductions, and calculates the net payable amount to the supplier.
* **Output:** Finalized farmer payment records flagged as 'Pending Payment'.
* **Validation:** * **No Negative Pay:** Excess deductions roll over to the next month as 'Arrears' instead of causing a negative balance.
  * **Deduction Cap:** Hard block on total deductions exceeding 75% of gross earnings without a supervisor override.
  * **Fraud Guard:** Flag payouts exceeding 300% of the farmer's 30-day average for manual review.

### FR-04 – Employee Payroll Management
* **Input:** Employee attendance, base salary, collector route completion data.
* **Process:** Calculates monthly salaries for office staff and tea collectors.
* **Output:** Finalized employee payroll ledger.
* **Validation:** * **Maker-Checker:** The user who generates the payroll batch cannot authorize the final bank transfer.
  * **Duplicate Lock:** Prevent generating a salary for the same Employee ID and Month twice.

### FR-05 – Payment Handling and Execution
* **Input:** Calculated net salary, selected payment method (Cash, Bank Transfer, Cheque), bank details (if applicable).
* **Process:** Executes the disbursement record. Updates the payment status from 'Pending' to 'Paid'. Generates a unique payment token for the transaction.
* **Output:** Completed payment ledger entry, receipt generation trigger, and SMS confirmation trigger.
* **Validation:** Cannot process a payment for a zero or negative balance; requires a valid, supported payment method.

### FR-06 – Loan & Advance Payment Management
* **Input:** Active loan profiles, scheduled installment amounts, requested advance payments.
* **Process:** Records issued advances and deducts scheduled loan repayments and advance recoveries from the monthly farmer payment.
* **Output:** Updated loan balances and advance recovery ledgers.
* **Validation:** * **Advance Limit:** Block new advances if the farmer's total debt exceeds their 3-month average collection value.
  * **Exact Recovery:** Auto-adjust the final installment to ensure the system never deducts more than the exact remaining balance.

### FR-07 – Fertilizer & Tea Deduction Management
* **Input:** Fertilizer distribution logs, personal tea issue logs.
* **Process:** Converts physical issuances into monetary deductions against the farmer's monthly payout using a strict deduction hierarchy.
* **Output:** Updated deduction ledgers.
* **Validation:** Values must be strictly positive integers or decimals.

### FR-08 – Receipt Generation
* **Input:** Finalized payment records, payment tokens.
* **Process:** Formats payment, deduction, and collection data into an official receipt layout.
* **Output:** Printable and downloadable (PDF) receipts bearing a unique verification token.
* **Validation:** Requires a completed and verified 'Paid' payment record.

### FR-09 – Report Generation
* **Input:** Historical system data (collections, payments, deductions).
* **Process:** Synthesizes raw data into structured daily, monthly, and route-specific reports.
* **Output:** Formatted business reports.
* **Validation:** Reports reflect only committed, immutable data to ensure audit accuracy.

### FR-10 – Data Synchronization & Conflict Resolution
* **Input:** Mobile collection payloads, authorization tokens, timestamps.
* **Process:** Authenticates the mobile device via token and merges incoming data with the desktop database. If a record conflict occurs, the system validates the timestamp.
* **Output:** Synchronized database, status notifications.
* **Validation:** * **Immutability:** Reject mobile edits to any record that is already part of a finalized 'Paid' batch.
  * **Clock Drift:** Reject mobile sync payloads if the device timestamp is more than 24 hours off from the server.
  * **Override Priority:** Manual office entries permanently lock out and overwrite conflicting mobile sync records.

### FR-11 – Manual Backup Entry
* **Input:** Keyboard entry of collection or payment data.
* **Process:** Bypasses mobile sync to allow direct administrative input during hardware/network failures.
* **Output:** System records flagged as manually entered.
* **Validation:** Enforces strict required-field and data-type validation.

---

## 3. Specific Requirement Categories

### 3.1 Token Generation & Security
* **Authentication Tokens:** Secure JWT (JSON Web Tokens) or equivalent for managing user sessions and API access.
* **Transaction Tokens:** Unique, non-sequential alphanumeric IDs generated for every completed payment and receipt to ensure traceability and prevent fraud.

### 3.2 Payment Processing & Handling Requirements
* **Automated Batching:** One-click batch calculation for all registered farmers at the end of the billing cycle.
* **Payment Methods:** Full support for recording Cash transactions, direct Bank Transfers, and Cheque issuances.
* **SMS Payment Confirmation:** Automatically trigger an SMS notification to the farmer via the configured SMS Gateway once a payment status is updated to 'Paid'.
* **Status Tracking:** System must track the lifecycle of a payment (e.g., *Pending, Processing, Paid, Failed*).
* **Audit Trail:** Every payment must securely log the office staff member who authorized the disbursement, a precise timestamp, and the transaction token.
* **Payment History:** Immutable logs of all past payments, retrievable and filterable by farmer ID, date range, or payment status.

### 3.3 Deduction Management Requirements
* Tracks real-time balances for Loans, Cash Advances, Fertilizer, and Tea advances.
* Automatically halts deductions once a specific loan or advance is fully recovered.
* Enforces a strict deduction hierarchy (e.g., Tea Issue -> Fertilizer -> Loans) if the gross payout is insufficient to cover all debts.

### 3.4 Office-Side User Actions
* Approve and resolve conflicts for synchronized data.
* Execute monthly payroll and farmer payouts, authorizing physical/digital payment disbursements under Dual Control.
* Configure system parameters (e.g., current tea purchasing rates, active banks).
* Issue receipts and export business intelligence reports.
* Manually input backup data with system override authority.

---

# Conclusion
The TeaRoutePay desktop application is responsible for managing accounting, reporting, payment processing, and business monitoring operations. The system must support automated enterprise-grade calculations, deduction management, strict synchronization conflict resolution, reporting, and backup entry functionality to improve operational efficiency, secure financial transactions, and reduce manual processing challenges.
