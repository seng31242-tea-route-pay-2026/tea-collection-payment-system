# Desktop Application Functional Requirements

## Overview

The TeaRoutePay desktop application is designed for office staff and business owners to securely manage tea collection accounting, token generation, payment handling, deductions, and reporting workflows. 

This document outlines the functional requirements for the office-side system, ensuring accurate monthly calculations, secure payment execution, and reliable manual backup operations, meeting the criteria for issue [SENG31242-#12].

---

## 1. Major Desktop Application Features

The system supports the following core capabilities:

| Feature | Description |
| :--- | :--- |
| **User Authentication & Token Generation** | Secure access management using generated authentication tokens for sessions and synchronization. |
| **Collection Record Management** | Interface to view, verify, and input daily tea collection logs. |
| **Salary Calculation** | Automated calculation of monthly farmer gross and net payouts. |
| **Payment Handling & Execution** | Comprehensive system for processing, recording, and tracking actual financial disbursements to farmers. |
| **Deduction Management** | System for tracking and applying loan, fertilizer, and personal tea issue deductions. |
| **Receipt Generation** | Automated creation of digital and printable receipts with unique transaction tokens. |
| **Report Generation** | Compilation of financial, operational, and historical reports. |
| **Data Synchronization** | Token-secured synchronization with mobile collection devices. |
| **Manual Backup Entry** | Provision for manual record entry during synchronization or device failures. |

---

## 2. Functional Requirements

### FR-01 – User Authentication & Token Generation
* **Input:** Username, Password.
* **Process:** Validates credentials and generates a secure session token. Generates API tokens for mobile synchronization.
* **Output:** Granted system access, session token, sync token.
* **Validation:** Credentials must match database records; tokens must expire after inactivity.

### FR-02 – Collection Record Management
* **Input:** Synchronized mobile data, manual entries.
* **Process:** Processes and securely stores daily collection weights.
* **Output:** Updated central database.
* **Validation:** Prevents duplicate collection entries for the same farmer/date.

### FR-03 – Monthly Salary Calculation
* **Input:** Total approved collection weight, current tea rates, aggregated deductions.
* **Process:** Computes gross total, subtracts deductions, and calculates the net payable amount. 
* **Output:** Finalized salary records flagged as 'Pending Payment'.
* **Validation:** Tea rates must be valid numeric values; final payout cannot be negative.

### FR-04 – Payment Handling and Execution
* **Input:** Calculated net salary, selected payment method (Cash, Bank Transfer, Cheque), bank details (if applicable).
* **Process:** Executes the disbursement record. Updates the payment status from 'Pending' to 'Paid'. Generates a unique payment token for the transaction.
* **Output:** Completed payment ledger entry, payment confirmation, and receipt generation trigger.
* **Validation:** Cannot process a payment for a zero or negative balance; requires a valid, supported payment method.

### FR-05 – Loan Deduction Management
* **Input:** Active loan profiles, scheduled installment amounts.
* **Process:** Deducts scheduled repayments from the monthly salary and updates outstanding capital.
* **Output:** Updated loan balances.
* **Validation:** Deductions cannot exceed the outstanding loan balance.

### FR-06 – Fertilizer & Tea Deduction Management
* **Input:** Fertilizer distribution logs, personal tea issue logs.
* **Process:** Converts physical issuances into monetary deductions against the farmer's monthly payout.
* **Output:** Updated deduction ledgers.
* **Validation:** Values must be strictly positive integers or decimals.

### FR-07 – Receipt Generation
* **Input:** Finalized payment records, payment tokens.
* **Process:** Formats payment, deduction, and collection data into an official receipt layout.
* **Output:** Printable and downloadable (PDF) receipts bearing a unique verification token.
* **Validation:** Requires a completed and verified 'Paid' payment record.

### FR-08 – Report Generation
* **Input:** Historical system data (collections, payments, deductions).
* **Process:** Synthesizes raw data into structured daily, monthly, and route-specific reports.
* **Output:** Formatted business reports.
* **Validation:** Reports reflect only committed, verified data.

### FR-09 – Data Synchronization
* **Input:** Mobile collection payloads, authorization tokens.
* **Process:** Authenticates the mobile device via token and merges incoming data with the desktop database.
* **Output:** Synchronized database, status notifications.
* **Validation:** Rejects payloads with invalid or expired tokens.

### FR-10 – Manual Backup Entry
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
* **Automated Payroll Batching:** One-click batch calculation for all registered farmers at the end of the billing cycle.
* **Payment Methods:** Full support for recording Cash transactions, direct Bank Transfers, and Cheque issuances.
* **Status Tracking:** System must track the lifecycle of a payment (e.g., *Pending, Processing, Paid, Failed*).
* **Audit Trail:** Every payment must securely log the office staff member who authorized the disbursement, a precise timestamp, and the transaction token.
* **Payment History:** Immutable logs of all past payments, retrievable and filterable by farmer ID, date range, or payment status.

### 3.3 Deduction Management Requirements
* Tracks real-time balances for Loans, Fertilizer, and Tea advances.
* Automatically halts deductions once a specific loan or advance is fully recovered.

### 3.4 Office-Side User Actions
* Approve synchronized data.
* Execute monthly payroll calculations and authorize physical/digital payment disbursements.
* Configure system parameters (e.g., current tea purchasing rates, active banks).
* Issue receipts and export business intelligence reports.
* Manually input backup data.


# Conclusion

The TeaRoutePay desktop application is responsible for managing accounting, reporting, payment processing, and business monitoring operations. The system must support automated calculations, deduction management, synchronization, reporting, and backup entry functionality to improve operational efficiency and reduce manual processing challenges.