# Desktop Application Functional Requirements

## Overview

The TeaRoutePay desktop application will be used by office staff and business owners to manage tea collection accounting operations, payment processing, deductions, reporting, and business monitoring activities.

The desktop system is designed to replace manual and semi-digital office workflows while improving accounting accuracy, reporting efficiency, and operational management.

This document identifies the functional requirements of the office-side desktop application.

---

# Purpose of the Desktop Application

The TeaRoutePay desktop application aims to:

- Manage tea collection records
- Calculate monthly farmer payments
- Manage deductions
- Generate receipts and reports
- Reduce manual accounting work
- Improve payment accuracy
- Support business monitoring
- Support manual backup data entry when necessary

---

# Major Desktop Application Features

The following major features are required in the desktop application.

| Feature | Description |
|---|---|
| User Authentication | Secure access for office staff and owners |
| Collection Record Management | View and manage tea collection records |
| Salary Calculation | Calculate monthly farmer payments |
| Loan Deduction Management | Manage loan deductions |
| Fertilizer Deduction Management | Manage fertilizer deductions |
| Tea Deduction Management | Manage tea issue deductions |
| Receipt Generation | Generate payment receipts |
| Report Generation | Generate operational and accounting reports |
| Farmer Record Management | Manage farmer profiles and information |
| Payment Record Management | Maintain payment history |
| Data Synchronization | Sync mobile collection records |
| Manual Backup Entry | Enter records manually if required |
| Data Validation | Validate accounting and collection records |

---

# Functional Requirements

## FR-01 – User Authentication

### Input
- Username
- Password

### Process
The system validates login credentials for office users.

### Output
- Access to the desktop system
- Invalid login warning messages

### Validation Rules
- Username cannot be empty
- Password cannot be empty

---

## FR-02 – Collection Record Management

### Input
- Collection records from mobile synchronization
- Manual collection records

### Process
The system stores and manages tea collection records.

### Output
- Updated collection database
- Collection summaries

### Validation Rules
- Duplicate records should be prevented
- Missing required fields should generate warnings

---

## FR-03 – Monthly Salary Calculation

### Input
- Tea collection totals
- Monthly tea rates
- Deductions

### Process
The system calculates monthly farmer payments automatically.

### Output
- Monthly salary records
- Payment summaries

### Validation Rules
- Tea rates must be valid
- Calculation errors should be detected

---

## FR-04 – Loan Deduction Management

### Input
- Loan information
- Deduction amounts

### Process
The system applies and tracks loan deductions.

### Output
- Updated loan balances
- Deduction summaries

### Validation Rules
- Deduction amounts must be numeric
- Invalid loan records should generate warnings

---

## FR-05 – Fertilizer Deduction Management

### Input
- Fertilizer distribution records
- Deduction values

### Process
The system calculates fertilizer-related deductions.

### Output
- Updated fertilizer deduction records

### Validation Rules
- Invalid deduction values are not allowed

---

## FR-06 – Tea Deduction Management

### Input
- Tea issue records
- Deduction amounts

### Process
The system applies tea-for-personal-use deductions.

### Output
- Updated deduction summaries

### Validation Rules
- Invalid deduction amounts should not be accepted

---

## FR-07 – Receipt Generation

### Input
- Payment information
- Farmer details

### Process
The system generates payment receipts.

### Output
- Printable receipts
- Digital receipts

### Validation Rules
- Required payment details must exist before receipt generation

---

## FR-08 – Report Generation

### Input
- Collection data
- Payment records
- Deduction records

### Process
The system generates operational and accounting reports.

### Output
- Daily reports
- Monthly reports
- Deduction reports
- Payment reports

### Validation Rules
- Reports should use validated system data only

---

## FR-09 – Farmer Record Management

### Input
- Farmer details
- Contact information

### Process
The system stores and updates farmer records.

### Output
- Updated farmer database

### Validation Rules
- Duplicate farmer IDs should not be allowed

---

## FR-10 – Payment Record Management

### Input
- Monthly salary data
- Payment transactions

### Process
The system stores and tracks payment history.

### Output
- Farmer payment history
- Payment summaries

### Validation Rules
- Invalid payment records should not be saved

---

## FR-11 – Data Synchronization

### Input
- Mobile application collection records

### Process
The system synchronizes records received from collector devices.

### Output
- Updated office database
- Synchronization status notifications

### Validation Rules
- Duplicate synchronization must be prevented

---

## FR-12 – Manual Backup Entry

### Input
- Manually entered collection or payment records

### Process
The system allows office staff to enter records manually when synchronization or mobile devices fail.

### Output
- Updated system records

### Validation Rules
- Manual entries must be validated before saving

---

## FR-13 – Data Validation and Error Handling

### Input
- User-entered accounting and collection data

### Process
The system validates records before saving.

### Output
- Validation messages
- Error notifications

### Validation Rules
- Required fields cannot be empty
- Invalid numeric values are not allowed

---

# Monthly Salary Calculation Requirements

The desktop application must support automated monthly salary calculations.

## Salary Calculation Inputs

The system should calculate payments using:
- Total tea collection weight
- Monthly tea rates
- Loan deductions
- Fertilizer deductions
- Tea deductions

## Expected Features

- Automatic calculations
- Monthly payment summaries
- Deduction summaries
- Payment verification support
- Reduced manual calculation errors

---

# Deduction Management Requirements

The system should support several deduction types.

## Loan Deductions
The system shall:
- Record loans
- Track loan balances
- Automatically apply deductions

## Fertilizer Deductions
The system shall:
- Record fertilizer distributions
- Apply fertilizer-related deductions

## Tea Deductions
The system shall:
- Record tea-for-personal-use transactions
- Apply tea deductions automatically

---

# Receipt Generation Requirements

The system should generate receipts containing:

- Farmer details
- Collection totals
- Deduction summaries
- Final payment amount
- Payment date

## Receipt Features

- Printable receipts
- Digital receipt support
- Clear payment summaries
- Payment verification support

---

# Report Generation Requirements

The desktop application should support operational and accounting reports.

## Required Reports

| Report Type | Purpose |
|---|---|
| Daily Collection Report | Monitor daily collection |
| Monthly Payment Report | Review farmer payments |
| Loan Deduction Report | Monitor loan balances |
| Fertilizer Distribution Report | Track fertilizer activities |
| Tea Deduction Report | Review tea deductions |
| Route Collection Report | Monitor collection routes |
| Farmer Collection History Report | View farmer collection trends |

---

# Manual Backup Data Entry Requirements

The system should support manual data entry when:
- Mobile synchronization fails
- Devices are unavailable
- Data recovery is required

## Expected Features

- Manual collection record entry
- Manual payment entry
- Validation support
- Duplicate prevention support

---

# Office-Side User Actions

The desktop application should support the following office activities:

- View synchronized collection records
- Verify collection information
- Calculate monthly payments
- Manage deductions
- Generate receipts
- Generate reports
- Manage farmer records
- Monitor business activities
- Enter backup records manually

---

# Expected Improvements with TeaRoutePay

The desktop application aims to improve office operations through:

- Reduced manual calculations
- Improved accounting accuracy
- Faster report generation
- Reduced duplicate data entry
- Better synchronization support
- Improved reporting functionality
- Improved payment management

---

# Conclusion

The TeaRoutePay desktop application is responsible for managing accounting, reporting, payment processing, and business monitoring operations. The system must support automated calculations, deduction management, synchronization, reporting, and backup entry functionality to improve operational efficiency and reduce manual processing challenges.