# Loan, Fertilizer, and Tea Deduction Rules Analysis

## Overview

The current tea collection and payment process includes several deduction types that affect the final monthly payment issued to farmers. These deductions are currently managed using manual records and the existing desktop accounting system.

This document analyses the deduction rules used by the client and identifies the business logic required for implementing accurate payment calculations in the TeaRoutePay system.


# Purpose of Deductions

The deduction process is used to:

- Recover farmer loans
- Recover fertilizer-related costs
- Recover tea issued for personal use
- Maintain accurate monthly payment calculations
- Support accounting and financial management activities


# Deduction Types

The following deduction categories were identified during workflow analysis and client discussions:

| Deduction Type | Purpose |
|----------------|---------|
| Loan Deduction | Recover farmer loan amounts |
| Fertilizer Deduction | Recover fertilizer distribution costs |
| Tea Deduction | Recover tea issued for personal use |


# Loan Deduction Rules

## Overview

Farmers may receive loans from the tea collection office. These loans are deducted gradually from the farmer’s monthly salary/payment.


## Loan Deduction Process

### Step 1 – Loan Issuing
The office records:
- Farmer details
- Loan amount
- Loan issue date
- Remaining balance

### Step 2 – Monthly Deduction
A predefined deduction amount or calculated amount is deducted from the monthly payment.

### Step 3 – Balance Update
After each payment cycle:
- Remaining loan balance is updated
- Deduction history is maintained

## Loan Deduction Data Fields

|    Data Field    |  Description           |
|------------------|------------------      |
| Loan ID          | Unique loan identifier |
| Farmer ID        |  Farmer identification |
| Loan Amount      |      Total issued loan |
| Deduction Amount |Monthly deduction value |
| Remaining Balance|Outstanding loan balance|
| Loan Issue Date  |   Date loan was issued |
| Payment Status   | Loan settlement status |


## Loan Deduction Business Rules

- Loan deductions shall not exceed the remaining balance.
- Loan deductions shall be recorded in payment history.
- The system shall update remaining balances automatically.
- Multiple loans may exist for a single farmer.
- Loan deductions must be included in monthly receipt summaries.


# Fertilizer Deduction Rules

## Overview

Farmers may receive fertilizer from the office, and the related cost is deducted from future monthly payments.


## Fertilizer Deduction Process

### Step 1 – Fertilizer Distribution
The office records:
- Farmer details
- Fertilizer type
- Quantity issued
- Cost amount

### Step 2 – Deduction Application
The fertilizer cost is deducted from the farmer’s payment during monthly salary processing.


## Fertilizer Deduction Data Fields

| Data Field       | Description     |
|------------------|-----------------|
| Distribution ID  | Fertilizer distribution identifier |
| Farmer ID        | Farmer identification |
| Fertilizer Type  |    Type of fertilizer |
| Quantity         |       Quantity issued |
| Cost Amount      | Total fertilizer cost |
| Distribution Date|  Date fertilizer was issued |
| Deduction Status | Deduction completion status |

---

## Fertilizer Deduction Business Rules

- Fertilizer deductions shall be linked to distribution records.
- The system shall maintain fertilizer deduction history.
- Fertilizer deductions must appear in payment receipts.
- The office shall be able to track unpaid fertilizer balances.

---

# Tea Deduction Rules

## Overview

Farmers may receive tea from the office for personal use. The value of this tea is deducted from monthly farmer payments.

---

## Tea Deduction Process

### Step 1 – Tea Issuing
The office records:
- Farmer details
- Tea quantity
- Tea value

### Step 2 – Monthly Deduction
The tea value is deducted from the farmer’s monthly payment.

---

## Tea Deduction Data Fields

| Data Field | Description |
|---|---|
| Tea Deduction ID | Tea deduction identifier |
| Farmer ID | Farmer identification |
| Tea Quantity | Issued tea quantity |
| Tea Value | Total deduction amount |
| Issue Date | Date tea was issued |
| Deduction Status | Deduction completion status |

---

## Tea Deduction Business Rules

- Tea deductions shall be included in salary calculations.
- Tea deduction history shall be maintained.
- Tea deductions shall appear on receipts.
- Multiple tea deduction records may exist for a farmer.

---

# Monthly Payment Calculation Logic

The final monthly payment should be calculated using:

```text id="u6m4de"
Final Payment =
(Total Tea Collection Weight × Monthly Tea Rate)
− Loan Deductions
− Fertilizer Deductions
− Tea Deductions