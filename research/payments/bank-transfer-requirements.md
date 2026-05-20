# Payment Process and Bank Transfer Requirements Analysis

## Overview

The current tea collection business process includes monthly salary calculations and bank payment preparation for farmers. Payment-related activities are currently handled using the existing desktop system together with manual bank processing methods.

This document analyses the existing payment workflow, bank transfer requirements, payment tracking needs, and manual fallback procedures required for the TeaRoutePay system.

---

# Current Payment Process

## Step 1 – Tea Collection Data Entry
Daily tea collection records are manually entered into the desktop system after collectors submit route books.

## Step 2 – Monthly Salary Calculation
Office staff calculate farmer payments based on:
- Total tea leaf weight
- Monthly tea rates
- Loan deductions
- Fertilizer deductions
- Tea-for-personal-use deductions

## Step 3 – Payment Verification
Office staff review and verify payment records before preparing salary payments.

## Step 4 – Bank Letter Preparation
The office prepares printed bank letters and payment documents containing farmer salary details.

## Step 5 – Bank Transfer Processing
Salary information is submitted to the bank for transfer processing.

## Step 6 – Payment Confirmation
Farmers receive payment information through receipts or direct communication from the office.

---

# Stakeholders Involved

| Stakeholder | Responsibility |
|---|---|
| Farmer | Receives monthly payments |
| Tea Collector | Supports collection record accuracy |
| Office Staff | Prepare salary calculations and payment records |
| Owner | Approves payments and monitors business operations |
| Bank | Processes farmer salary transfers |

---

# Payment Data Requirements

The system should maintain the following payment-related information for each farmer.

| Data Item | Description |
|---|---|
| Farmer ID | Unique farmer identification |
| Farmer Name | Farmer full name |
| Bank Account Number | Farmer bank account details |
| Bank Name | Bank information |
| Monthly Tea Collection Total | Total collected tea weight |
| Tea Rate | Monthly tea rate |
| Loan Deductions | Loan deduction amounts |
| Fertilizer Deductions | Fertilizer-related deductions |
| Tea Deductions | Tea-for-personal-use deductions |
| Final Salary Amount | Final payment value |
| Payment Status | Current payment progress |
| Payment Date | Salary payment date |
| SMS Notification Status | Payment confirmation tracking |

---

# Bank Transfer Requirements

The TeaRoutePay system should support bank transfer preparation and payment management activities.

## Required Features

### 1. Payment Record Preparation
The system shall generate payment records for all eligible farmers.

### 2. Bank Transfer Data Generation
The system shall prepare bank-compatible payment data for salary processing.

### 3. Payment Verification Support
The system shall allow office staff and owners to verify payment details before approval.

### 4. Salary Approval Workflow
The system shall support payment approval before bank submission.

### 5. Payment History Management
The system shall maintain historical salary payment records.

### 6. SMS Notification Support
The system shall support payment confirmation SMS notifications after successful payment processing.

---

# Payment Approval Flow

The current and proposed workflow includes several approval stages.

## Proposed Approval Process

1. Monthly salary calculations are generated.
2. Office staff review farmer payment records.
3. Deduction details are verified.
4. Owner or authorized staff approve payments.
5. Bank transfer records are prepared.
6. Payments are submitted to the bank.
7. Payment status is updated after processing.
8. SMS notifications are sent to farmers.

---

# Payment Status Tracking Requirements

The system should support payment tracking using status values.

## Required Payment Status Values

| Status | Description |
|---|---|
| Pending | Payment created but not reviewed |
| Verified | Payment verified by office staff |
| Approved | Payment approved for bank transfer |
| Submitted | Payment submitted to the bank |
| Processing | Bank processing in progress |
| Completed | Payment successfully transferred |
| Failed | Payment transfer failed |
| Corrected | Payment corrected and resubmitted |

---

# Manual Payment Fallback Requirements

The system should support manual fallback procedures when automated processing fails.

## Required Fallback Support

### 1. Manual Payment Verification
Office staff should be able to manually verify payment records.

### 2. Manual Payment Correction
Incorrect salary calculations should be editable before approval.

### 3. Manual Bank Submission
Printed bank letters should still be supported if digital submission is unavailable.

### 4. Offline Record Access
Payment records should remain accessible during connectivity interruptions.

### 5. Backup Record Support
The system should support backup and recovery of payment records.

---

# Payment Failure and Correction Scenarios

Several situations may require payment corrections or reprocessing.

## Possible Failure Scenarios

- Incorrect bank account numbers
- Duplicate payment submissions
- Incorrect deduction calculations
- Missing farmer payment records
- Bank transfer failures
- Connectivity interruptions during synchronization

## Required Correction Features

- Ability to update incorrect payment details
- Payment resubmission support
- Failed payment tracking
- Audit trail support for payment corrections
- Notification support after successful correction

---

# Expected Improvements with TeaRoutePay

The TeaRoutePay system aims to improve payment processing through:

- Reduced manual paperwork
- Better payment transparency
- Improved payment tracking
- Faster salary processing
- Improved deduction accuracy
- SMS-based payment confirmation
- Better synchronization between collection and accounting systems
- Reduced human errors during salary processing

---

# Conclusion

The current payment process depends heavily on manual verification, printed bank letters, and repeated office work. TeaRoutePay aims to modernize payment processing by improving payment tracking, salary preparation, bank transfer support, and communication with farmers while maintaining fallback procedures for operational reliability.