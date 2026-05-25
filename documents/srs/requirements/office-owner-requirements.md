# Owner and Office Staff Requirements

## Overview

Owners and office staff are responsible for managing tea collection records, accounting activities, deductions, monthly payments, receipts, and business monitoring operations.

Currently, office staff manually re-enter daily collection records into the desktop system after route collection activities are completed. The TeaRoutePay system aims to improve accounting accuracy, reduce manual workload, and modernize business management processes.

This document identifies owner and office staff requirements, monthly payment calculation needs, deduction handling requirements, and reporting expectations.

---

# Current Responsibilities of Office Staff

Office staff currently perform the following activities:

- Receive route books from tea collectors
- Manually enter collection records into the desktop system
- Calculate monthly payments
- Manage loan deductions
- Manage fertilizer deductions
- Manage tea-for-personal-use deductions
- Generate payment receipts
- Maintain accounting records
- Prepare reports for business monitoring
- Coordinate payment processing activities

---

# Current Workflow Challenges

## 1. Duplicate Data Entry
Collection data is first written manually and later re-entered into the desktop system.

## 2. Human Error Risk
Manual calculations and record entry may result in:
- Incorrect payments
- Missing records
- Duplicate entries
- Incorrect deductions

## 3. Time-Consuming Monthly Processing
Month-end salary calculations and report preparation require significant manual effort.

## 4. Limited Automation
Several business operations still depend on manual verification and calculations.

## 5. Limited Reporting Capabilities
The current system has limited reporting and business monitoring functionality.

## 6. Outdated User Interface
The desktop system interface is difficult for new users to operate efficiently.

---

# Office and Owner Functional Requirements

## FR-01 – User Authentication
The system shall allow owners and office staff to securely access the system.

## FR-02 – Collection Record Management
The system shall allow office staff to view, manage, and verify tea collection records.

## FR-03 – Monthly Salary Calculation
The system shall calculate monthly farmer payments based on:
- Tea collection records
- Monthly tea rates
- Applied deductions

## FR-04 – Office-Based Payment Processing
The system shall allow office staff to review, verify, and process farmer payments using the office computer system.

## FR-05 – Loan Deduction Management
The system shall record and manage farmer loan deductions.

## FR-06 – Fertilizer Deduction Management
The system shall manage fertilizer distribution records and related deductions.

## FR-07 – Tea Deduction Management
The system shall manage tea-for-personal-use deductions.

## FR-08 – Payment Record Management
The system shall maintain farmer payment history records.

## FR-09 – Receipt Generation
The system shall generate printable and digital payment receipts.

## FR-10 – Report Generation
The system shall generate business and operational reports.

## FR-11 – Route Data Synchronization
The system shall synchronize collection data received from mobile devices.

## FR-12 – SMS Notification Support
The system shall support sending payment confirmation SMS notifications to farmers.

## FR-13 – Data Validation
The system shall validate records to reduce duplicate entries and calculation errors.

---

# Monthly Payment Calculation Requirements

The TeaRoutePay system should support automated monthly payment calculations.

## Salary Calculation Inputs

The system should calculate payments using:
- Total tea leaf weight
- Monthly tea rates
- Loan deductions
- Fertilizer deductions
- Tea deductions

## Expected Features

- Automatic payment calculations
- Deduction summaries
- Monthly payment history
- Payment verification support
- Error reduction during calculations

---

# Deduction Management Requirements

The system should support several deduction types.

## 1. Loan Deductions
The system shall:
- Maintain loan records
- Track outstanding balances
- Automatically apply loan deductions

## 2. Fertilizer Deductions
The system shall:
- Record fertilizer distributions
- Apply related deductions during salary calculations

## 3. Tea-for-Personal-Use Deductions
The system shall:
- Record tea issued for personal use
- Apply related deductions to monthly payments

---

# Receipt Generation Requirements

The system should generate payment receipts containing:

- Farmer details
- Collection totals
- Deduction summaries
- Final payment amount
- Payment date

## Expected Receipt Features

- Printable receipt support
- Digital receipt generation
- Clear payment summaries
- Easy verification support

---

# Report Generation Requirements

The system should support operational and accounting reports.

## Required Reports

| Report Type | Purpose |
|---|---|
| Daily Collection Report | Monitor daily tea collection |
| Monthly Payment Report | Review farmer payments |
| Loan Deduction Report | Track loan balances |
| Fertilizer Distribution Report | Monitor fertilizer-related activities |
| Tea Deduction Report | Review tea deductions |
| Route Collection Report | Monitor route performance |
| Farmer Collection History Report | View farmer collection trends |

---

# Business Monitoring Requirements

Owners require system support for business monitoring and operational management.

## Monitoring Needs

- Daily collection monitoring
- Payment tracking
- Deduction tracking
- Farmer activity monitoring
- Route performance monitoring
- Business reporting and analysis

---

# Expected Improvements with TeaRoutePay

The TeaRoutePay system aims to improve office operations through:

- Reduced duplicate data entry
- Improved accounting accuracy
- Faster salary processing
- Better synchronization between field and office operations
- Improved reporting functionality
- Better usability and maintainability
- Reduced manual workload
- Improved payment transparency

---

# Conclusion

Owners and office staff are responsible for managing core business and accounting operations. The current workflow depends heavily on manual processing and duplicate data entry. TeaRoutePay aims to modernize these operations through improved automation, synchronization, reporting, and payment management functionality.