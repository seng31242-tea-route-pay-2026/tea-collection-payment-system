# Loan, Advance, Fertilizer, and Tea Deduction Rules Analysis

## Overview
The current tea collection and payment process includes several deduction types that affect the final monthly vendor payout issued to farmers. These deductions are currently managed using manual records and the existing desktop accounting system.

This document analyses the deduction rules used by the client and identifies the enterprise business logic required for implementing accurate payout calculations, strict deduction hierarchies, and arrears management in the TeaRoutePay system.

## Purpose of Deductions
The deduction process is used to:
* Recover farmer loans and cash advances
* Recover fertilizer-related distribution costs
* Recover tea issued for personal use
* Maintain accurate monthly payout calculations without generating negative balances
* Support accounting and financial management activities

## Deduction Types
The following deduction categories were identified during workflow analysis:

| Deduction Type | Purpose | Priority Level |
| :--- | :--- | :--- |
| **Tea Deduction** | Recover tea issued for personal use | Priority 1 (Highest) |
| **Fertilizer Deduction** | Recover fertilizer distribution costs | Priority 2 |
| **Advance Deduction** | Recover short-term cash advances | Priority 3 |
| **Loan Deduction** | Recover long-term farmer loan installments | Priority 4 (Lowest) |

---

## 1. Loan Deduction Rules
Farmers may receive long-term loans from the tea collection office. These loans are deducted gradually via scheduled installments from the farmer’s monthly payout.

### Loan Deduction Data Fields
| Data Field | Description |
| :--- | :--- |
| **Loan ID** | Unique loan identifier |
| **Farmer ID** | Farmer identification |
| **Loan Amount** | Total issued loan principal |
| **Installment Amount** | Scheduled monthly deduction value |
| **Remaining Balance** | Outstanding loan balance |
| **Loan Issue Date** | Date loan was issued |
| **Status** | Active, Defaulted, or Settled |

### Business Rules
* The system shall automatically adjust the final installment to ensure the deduction never exceeds the remaining balance.
* Multiple active loans may exist for a single farmer and must be aggregated.
* Deductions must be logged in the immutable payment history.

---

## 2. Cash Advance Deduction Rules
Farmers frequently request short-term cash advances against their uncalculated monthly tea collections.

### Advance Deduction Data Fields
| Data Field | Description |
| :--- | :--- |
| **Advance ID** | Unique advance identifier |
| **Farmer ID** | Farmer identification |
| **Advance Amount** | Total cash value issued |
| **Issue Date** | Date advance was issued |
| **Recovery Status** | Pending or Recovered |

### Business Rules
* Advances are short-term and must be recovered in full during the immediate next billing cycle.
* The system must block new advance requests if the farmer’s current total debt exceeds a configured threshold of their historical average collection.

---

## 3. Fertilizer Deduction Rules
Farmers receive fertilizer from the office, and the related cost is deducted from future monthly payouts.

### Fertilizer Deduction Data Fields
| Data Field | Description |
| :--- | :--- |
| **Distribution ID** | Fertilizer distribution identifier |
| **Farmer ID** | Farmer identification |
| **Fertilizer Type** | Type of fertilizer |
| **Quantity** | Quantity issued (kg/bags) |
| **Cost Amount** | Total fiat cost of the fertilizer |
| **Distribution Date** | Date fertilizer was issued |

### Business Rules
* Fertilizer deductions shall be strictly linked to inventory distribution records.
* The office shall be able to track unpaid fertilizer balances rolled over into Arrears.

---

## 4. Tea Deduction Rules
Farmers may receive packaged tea from the office for personal use. The value is deducted from monthly payouts.

### Tea Deduction Data Fields
| Data Field | Description |
| :--- | :--- |
| **Tea Deduction ID** | Tea deduction identifier |
| **Farmer ID** | Farmer identification |
| **Tea Quantity** | Issued tea quantity |
| **Tea Value** | Total deduction amount (fiat value) |
| **Issue Date** | Date tea was issued |

### Business Rules
* Tea deductions hold the highest recovery priority in the calculation hierarchy.
* Multiple tea deduction records per month must be aggregated prior to calculation.

---

## Monthly Payout Calculation & Arrears Logic

The final monthly payment relies on a strict deduction hierarchy to prevent negative balances. 

**Step 1: Calculate Gross Earnings**
`Gross Payout = (Total Approved Tea Weight × Monthly Tea Rate)`

**Step 2: Apply Strict Deduction Hierarchy**
Deductions are subtracted from the `Gross Payout` sequentially. If at any point the `Gross Payout` reaches LKR 0.00, the system must halt further deductions.

1. Subtract **Tea Deductions**
2. Subtract **Fertilizer Deductions**
3. Subtract **Cash Advances**
4. Subtract **Loan Installments**

**Step 3: Arrears Carry-Forward**
`Final Net Payout = Max(0, Gross Payout - Total Applied Deductions)`

Any unrecovered deduction amounts (due to the `Gross Payout` hitting 0) must NOT result in a negative payout. Instead, unrecovered amounts are automatically carried forward to the next billing cycle under an **'Arrears'** ledger.
