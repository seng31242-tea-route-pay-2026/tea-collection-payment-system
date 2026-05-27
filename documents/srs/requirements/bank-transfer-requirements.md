# Payment Process and Bank Transfer Requirements Analysis

## Overview
The current tea collection business process includes monthly payout calculations and bank payment preparation for farmers. Payment-related activities are currently handled using the existing desktop system together with manual bank processing methods.

This document analyses the existing payment workflow, bank transfer requirements, payment tracking needs, and manual fallback procedures required for the TeaRoutePay system.

## Current Payment Process
* **Step 1 – Tea Collection Data Entry:** Daily tea collection records are manually entered into the desktop system after collectors submit route books.
* **Step 2 – Monthly Payout Calculation:** Office staff calculate farmer vendor payments based on:
  * Total tea leaf weight
  * Monthly tea rates
  * Loan deductions
  * Advance payment recoveries
  * Fertilizer deductions
  * Tea-for-personal-use deductions
* **Step 3 – Payment Verification:** Office staff review and verify payment records before preparing the final batch.
* **Step 4 – Bank Letter Preparation:** The office prepares printed bank letters and payment documents containing farmer payout details.
* **Step 5 – Bank Transfer Processing:** Payout information is submitted to the bank for transfer processing.
* **Step 6 – Payment Confirmation:** Farmers receive payment information through receipts or direct communication from the office.

## Stakeholders Involved
| Stakeholder | Responsibility |
| :--- | :--- |
| **Farmer** | Receives monthly vendor payments |
| **Tea Collector** | Supports collection record accuracy |
| **Office Staff** | Prepares payout calculations and payment records |
| **Owner** | Approves payments and monitors business operations |
| **Bank** | Processes farmer automated bank transfers |

## Payment Data Requirements
The system should maintain the following payment-related information for each farmer:

| Data Item | Description |
| :--- | :--- |
| **Farmer ID** | Unique farmer identification |
| **Farmer Name** | Farmer full name |
| **Bank Account Number** | Farmer bank account details |
| **Bank Name & Branch Code** | Routing information required for SLIPS/CEFTS transfers |
| **Monthly Tea Collection Total** | Total collected tea weight |
| **Tea Rate** | Monthly tea rate |
| **Loan Deductions** | Loan deduction amounts |
| **Advance Recoveries** | Deductions for previously issued cash advances |
| **Fertilizer Deductions** | Fertilizer-related deductions |
| **Tea Deductions** | Tea-for-personal-use deductions |
| **Final Payout Amount** | Final net payment value |
| **Payment Status** | Current payment progress state |
| **Payment Date** | Date of payout execution |
| **SMS Notification Status** | Payment confirmation tracking |

## Bank Transfer Requirements
The TeaRoutePay system should support bank transfer preparation and payment management activities.

### Required Features
1. **Payment Record Preparation:** The system shall generate payment records for all eligible farmers.
2. **Bank Transfer Data Generation:** The system shall prepare bank-compatible export files (e.g., CSV, Excel) formatted to local corporate banking standards.
3. **Payment Verification Support:** The system shall allow office staff and owners to verify payment details before approval.
4. **Payout Approval Workflow:** The system shall enforce a Maker-Checker approval workflow before bank submission.
5. **Payment History Management:** The system shall maintain immutable historical payout records.
6. **SMS Notification Support:** The system shall support payment confirmation SMS notifications after successful payment processing.

## Payment Approval Flow
The proposed workflow includes several approval stages enforcing strict Segregation of Duties (Dual Control):

1. Monthly payout calculations are generated (The Maker).
2. Office staff review farmer payment records.
3. Deduction details and advance recoveries are verified.
4. Owner or authorized staff approve payments (The Checker - must be a different user).
5. Bank transfer export files are prepared.
6. Payments are submitted to the banking portal.
7. Payment status is updated in the system after processing.
8. SMS notifications are triggered to farmers.

## Payment Status Tracking Requirements
The system should support payment tracking using strict state values:

| Status | Description |
| :--- | :--- |
| **Pending** | Payment created but not reviewed |
| **Verified** | Payment verified by office staff |
| **Approved** | Payment approved for bank transfer (Locked for editing) |
| **Submitted** | Payment file submitted to the bank |
| **Processing** | Bank processing in progress |
| **Completed** | Payment successfully transferred |
| **Failed** | Payment transfer failed at the bank level |
| **Corrected** | Payment corrected via an adjustment record and resubmitted |

## Manual Payment Fallback Requirements
The system should support manual fallback procedures when automated processing fails:

1. **Manual Payment Verification:** Office staff should be able to manually verify payment records.
2. **Manual Payment Correction:** Incorrect calculations should be editable *before* approval.
3. **Manual Bank Submission:** Printed bank authorization letters must still be supported if digital CSV/API submission is unavailable.
4. **Offline Record Access:** Payment ledgers should remain accessible during internet connectivity interruptions.
5. **Backup Record Support:** The system should support local backup and recovery of payment records.

## Payment Failure and Correction Scenarios
Several situations may require payment corrections or reprocessing:

* Incorrect bank account numbers or missing branch codes
* Duplicate payment submissions
* Incorrect deduction/advance calculations
* Missing farmer payment records
* Bank API or transfer file rejections
* Connectivity interruptions during synchronization

### Required Correction Features
* Ability to update incorrect payment details (Prior to 'Approved' status).
* Support for explicit Reversal/Adjustment records for 'Failed' transfers.
* Failed payment logging and tracking.
* Audit trail support logging the user ID for all payment corrections.
* Notification support after successful correction.

## Expected Improvements with TeaRoutePay
The TeaRoutePay system aims to improve payment processing through:
* Reduced manual paperwork and physical bank letters
* Better payment transparency and auditability
* Faster, automated payout processing
* Improved deduction and advance recovery accuracy
* Automated SMS-based payment confirmation
* Enforced Maker-Checker security controls
* Reduced human errors during financial calculations

## Conclusion
The current payment process depends heavily on manual verification, printed bank letters, and repeated office work. TeaRoutePay aims to modernize payment processing by improving payment tracking, supplier payout preparation, automated corporate bank file generation, and communication with farmers, while maintaining robust manual fallback procedures for operational reliability.
