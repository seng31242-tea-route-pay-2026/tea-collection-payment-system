# Monthly Receipt Generation Requirements

## Overview

The current tea collection process provides farmers with monthly payment receipts after salary calculations are completed. These receipts contain payment information, deductions, and tea collection summaries.

The TeaRoutePay system aims to improve receipt clarity, accuracy, and transparency by generating better-structured receipts that clearly display tea collection totals, deductions, monthly rates, and final payment values.

This document identifies the receipt generation requirements for the TeaRoutePay system.

# Purpose of Monthly Receipts

Monthly receipts are important because they help farmers:

- Verify tea collection totals
- Understand payment calculations
- Review deduction details
- Confirm final payment amounts
- Maintain personal payment records

Receipts also support office accounting and payment verification processes.

# Current Receipt Process

Currently, office staff generate receipts after monthly salary calculations are completed using the existing desktop system.

The process includes:

1. Manual verification of collection records
2. Monthly salary calculation
3. Deduction calculation
4. Receipt generation and printing
5. Distribution of receipts to farmers

The current receipt format has limited clarity and depends heavily on manual verification.

# Required Receipt Fields

The TeaRoutePay system should generate receipts containing the following information.

| Field | Description |
|---|---|
| Receipt Number | Unique receipt identifier |
| Farmer ID | Unique farmer identification number |
| Farmer Name | Farmer full name |
| Collection Month | Relevant payment month |
| Total Tea Weight | Total tea leaf weight collected |
| Monthly Tea Rate | Tea payment rate per unit |
| Gross Payment Amount | Total payment before deductions |
| Loan Deduction | Loan-related deduction amount |
| Fertilizer Deduction | Fertilizer-related deduction amount |
| Tea Deduction | Tea-for-personal-use deduction amount |
| Other Deductions | Additional deductions if applicable |
| Total Deductions | Combined deduction amount |
| Net Payment Amount | Final payment after deductions |
| Payment Date | Date of payment processing |
| Receipt Generation Date | Date receipt was generated |

# Monthly Total Calculation Requirements

The system should calculate monthly payment totals accurately.

## Required Calculation Inputs

The system shall calculate totals using:

- Daily tea collection records
- Monthly tea rates
- Applicable deductions
- Farmer-specific payment adjustments if required

## Required Calculation Features

- Automatic monthly total calculation
- Accurate tea weight summation
- Validation of missing or duplicate records
- Support for updated monthly tea rates
- Automatic deduction calculations

# Deduction Display Requirements

The receipt should clearly display all deductions applied to the farmer payment.

## Required Deduction Types

### 1. Loan Deductions
Display:
- Loan deduction amount
- Remaining balance if applicable

### 2. Fertilizer Deductions
Display:
- Fertilizer-related deduction values

### 3. Tea-for-Personal-Use Deductions
Display:
- Tea deduction amount

### 4. Other Deductions
Display:
- Additional charges or adjustments if applicable

# Final Net Payment Display Requirements

The receipt should clearly highlight the final payment amount.

## Required Features

- Clear separation between gross and net payment
- Total deductions displayed before final amount
- Easy-to-read payment summary section
- Proper alignment of monetary values

The final payment section should help farmers easily understand:
- Total earnings
- Total deductions
- Final payable amount

# Receipt Format Requirements

The TeaRoutePay system should support well-structured receipt formatting.

## Formatting Requirements

- Clean and readable layout
- Proper section separation
- Consistent field alignment
- Easy-to-read font sizes
- Printable format support
- Digital receipt generation support

## Receipt Sections

The receipt should contain:

1. Farmer Information Section
2. Tea Collection Summary Section
3. Deduction Summary Section
4. Final Payment Summary Section
5. Receipt Metadata Section

# Sample Receipt Structure

--------------------------------------------------
                TeaRoutePay Receipt
--------------------------------------------------

Receipt No     : REC-2026-00125
Farmer ID      : F-1004
Farmer Name    : Kamal Perera
Month          : May 2026

--------------------------------------------------
Tea Collection Summary
--------------------------------------------------

Total Tea Weight      : 1240 Kg
Monthly Tea Rate      : Rs. 180.00
Gross Payment         : Rs. 223,200.00

--------------------------------------------------
Deduction Summary
--------------------------------------------------

Loan Deduction        : Rs. 10,000.00
Fertilizer Deduction  : Rs. 2,500.00
Tea Deduction         : Rs. 1,200.00

Total Deductions      : Rs. 13,700.00

--------------------------------------------------
Final Payment Summary
--------------------------------------------------

Net Payment Amount    : Rs. 209,500.00

--------------------------------------------------

Payment Date          : 30 May 2026
Generated Date        : 31 May 2026

--------------------------------------------------