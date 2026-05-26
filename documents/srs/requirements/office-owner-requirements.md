# Owner and Office Staff Requirements

## Overview
Owners and office staff represent the primary administrative users of the TeaRoutePay system. They manage tea collection records, deductions, vendor payouts, employee payroll, factory sales, and comprehensive business reporting. TeaRoutePay aims to reduce manual work, enforce financial accuracy, and support high-level business intelligence and profit monitoring.

## Office Staff & Owner Responsibilities
* Receive and verify route synchronization data from field collectors.
* Calculate and execute monthly vendor payouts (for farmers).
* Calculate and execute monthly employee payroll (for collectors and office staff).
* Manage business deductions, including loans, advances, fertilizer, and tea issues.
* Record bulk tea sales to designated Tea Factories/Estates.
* Generate receipts and payment bank transfer files.
* Maintain strict accounting ledgers and audit trails.
* Generate and analyze comprehensive business intelligence reports.

## Current Workflow Challenges
* Manual data entry and high risk of human calculation errors.
* Time-consuming monthly financial processing.
* Lack of real-time Profit & Loss (P&L) visibility.
* Inability to easily track profit margins between Farmer Purchase Price and Factory Sell Price.
* Limited reporting support for individual historical tracking.
* Disconnected tracking of employee payroll vs. supplier payouts.

## Functional Requirements

### FR-01 – User Authentication & Role-Based Access
Office staff and owners must securely access the system, with strict Role-Based Access Control (RBAC) restricting sensitive financial reports and approvals to the 'Owner' role.

### FR-02 – Collection Record Management
The system shall manage, verify, and resolve synchronization conflicts for daily field collection records.

### FR-03 – Farmer Vendor Payout Calculation
The system shall accurately calculate monthly farmer payments based on approved gross weights, dynamic tea purchasing rates, and strict deduction hierarchies.

### FR-04 – Employee Payroll Management
The system shall manage the monthly salary processing for internal business employees, including field tea collectors and office staff.

### FR-05 – Deduction & Advance Management
The system shall manage and track real-time balances for:
* Long-term Loan deductions
* Short-term Cash Advances
* Fertilizer distribution deductions
* Personal Tea issue deductions

### FR-06 – Factory Sales Management
The system shall record outbound bulk tea sales to external Tea Factories, tracking the selling price, total weight supplied, and payment status from the factories.

### FR-07 – Receipt & Mandate Generation
The system shall generate printable farmer receipts and structured corporate bank transfer files (e.g., CSV/Excel).

### FR-08 – Comprehensive Report Generation
The system shall generate dynamic financial, operational, and individual reports with custom date-range filtering.

### FR-09 – SMS Notifications
The system shall automatically trigger SMS notifications to farmers upon successful collection sync and monthly payout execution.

---

## Vendor Payout & Employee Payroll Calculation Requirements
The system must separate external supplier payments from internal employee salaries. 
* **Farmer Vendor Payouts:** Calculated using approved tea collection totals, dynamic monthly tea purchasing rates, and a strict deduction hierarchy (Tea Issues -> Fertilizer -> Cash Advances -> Loans).
* **Employee Payroll:** Calculated using collector route completion data, office staff attendance, and base salary configurations.

**Expected features:**
* Automated gross-to-net calculations.
* Automated deduction and advance recovery summaries.
* Negative carry-forward logic (Arrears) to prevent negative payouts.
* Immutable payment history tracking and audit trails.
* Error reduction via Maker-Checker (Dual Control) authorization.

## Receipt & Bank Mandate Requirements
The system must generate physical/digital documentation for all financial transactions.

**Receipts and Mandates should include:**
* Farmer/Employee details and unique IDs.
* Total collection weights (for farmers) or attendance (for employees).
* Itemized deduction and advance recovery summaries.
* Final net payment amount.
* Payment execution date and unique transaction security token.

## Business Monitoring & Advanced Reporting Needs
To provide the Owner with actionable business intelligence, the system must support daily monitoring and generate comprehensive reports filterable by specific custom time periods (e.g., weekly, monthly, annual):

### 1. Financial & Profitability Reports
* **Profit & Loss (P&L) Statement:** A master summary calculating total revenue (Sales to Factories) minus total costs (Farmer Payouts + Employee Payroll + Operational Expenses).
* **Factory Sales & Margin Report:** Details total weight sold to specific factories, the factory purchasing rate, and the exact profit margin retained by the business.
* **Business Expense Report:** Tracking of daily operational costs (e.g., vehicle fuel, office supplies).

### 2. Operational & Entity Reports
* **Bought Goods (Supplier) Summary:** Aggregated data on total tea purchased from farmers.
* **Employee Payroll Report:** Summary of all internal salaries paid to collectors and staff.
* **Deduction & Debt Ledger:** Total outstanding capital for all active farmer loans and unrecovered advances.
* **Collector Performance Report:** Route efficiency tracking, showing total weight collected by specific collectors over a given time period.

### 3. Individual Specific Reports
* **Individual Farmer Ledger:** A highly detailed, individual summary for a specific farmer over a custom date range, showing every daily collection (and which collector received it), every deduction applied, and complete payout history.

## Expected Improvements
Implementing the TeaRoutePay desktop architecture will result in:
* **Financial Clarity:** Instant visibility into Factory Sales vs. Farmer Costs to determine real-time profitability.
* **Drastically reduced manual administrative work.**
* **Faster, automated financial processing** for both vendors and employees.
* **Reliable synchronization** between offline field data and the central office.
* **Deep business intelligence** and profit margin reporting.
* **Better payment transparency** via automated SMS notifications.
* **Improved usability and strict financial security.**

## Conclusion
TeaRoutePay will modernize office operations by transforming a manual tracking process into a robust financial management system. By improving accounting accuracy, offline-to-online synchronization, comprehensive reporting (including factory sales), and separating vendor payment management from employee payroll, the system will drastically reduce manual processing tasks and secure the business's financial integrity.
