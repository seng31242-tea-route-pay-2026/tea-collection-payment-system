# Use Case Descriptions

## Overview

This document contains the major use case descriptions for the TeaRoutePay system. The use case model identifies how different actors interact with the system to perform tea collection, payment management, reporting, and synchronization activities.

---

# UC-01 – Login to System

## Actor
- Tea Collector
- Office Staff
- Owner

## Description
Allows authorized users to access the TeaRoutePay system securely.

## Preconditions
- User account exists
- User has valid login credentials

## Main Flow
1. User opens the system
2. User enters username and password
3. System validates credentials
4. System grants access

## Postconditions
- User is authenticated
- User dashboard is displayed

---

# UC-02 – Scan Farmer QR Code

## Actor
- Tea Collector

## Description
Allows the tea collector to identify a farmer using a QR code.

## Preconditions
- Collector is logged in
- Farmer QR code exists

## Main Flow
1. Collector opens QR scanner
2. Collector scans QR code
3. System retrieves farmer details
4. Farmer information is displayed

## Postconditions
- Correct farmer is identified

---

# UC-03 – Record Tea Collection

## Actor
- Tea Collector

## Description
Allows collectors to record tea collection details.

## Preconditions
- Farmer is identified
- Collector is logged in

## Main Flow
1. Collector enters tea weight
2. Collector confirms collection details
3. System saves collection record

## Postconditions
- Tea collection data is stored locally or synchronized

---

# UC-04 – Synchronize Route Data

## Actor
- Tea Collector

## Description
Allows offline route data to synchronize with the central system.

## Preconditions
- Unsynchronized records exist
- Internet connection is available

## Main Flow
1. Collector starts synchronization
2. System uploads local records
3. System validates synchronization
4. Synchronization completes

## Postconditions
- Central database is updated

---

# UC-05 – Calculate Monthly Payments

## Actor
- Office Staff

## Description
Calculates farmer monthly payments using collection and deduction data.

## Preconditions
- Monthly collection data exists
- Monthly tea rate is available

## Main Flow
1. Office staff selects calculation period
2. System retrieves collection data
3. System applies deductions
4. System calculates final payment

## Postconditions
- Monthly payment records are generated

---

# UC-06 – Manage Farmer Deductions

## Actor
- Office Staff

## Description
Allows management of loan, fertilizer, and tea deductions.

## Preconditions
- Farmer account exists

## Main Flow
1. Office staff selects farmer
2. Office staff enters deduction details
3. System validates deduction
4. System saves deduction record

## Postconditions
- Deduction records are updated

---

# UC-07 – Generate Payment Receipt

## Actor
- Office Staff

## Description
Generates payment receipts for farmers.

## Preconditions
- Payment calculation completed

## Main Flow
1. Office staff selects farmer payment
2. System generates receipt
3. Receipt is printed or shared digitally

## Postconditions
- Receipt is generated successfully

---

# UC-08 – Generate Reports

## Actor
- Office Staff
- Owner

## Description
Generates operational and accounting reports.

## Preconditions
- Collection and payment data exists

## Main Flow
1. User selects report type
2. System retrieves report data
3. System generates report

## Postconditions
- Requested report is displayed or exported

---

# UC-09 – Send SMS Notification

## Actor
- SMS Service

## Description
Sends SMS notifications related to payments and collection updates.

## Preconditions
- Farmer mobile number exists

## Main Flow
1. System prepares SMS message
2. SMS service receives request
3. SMS notification is sent

## Postconditions
- Farmer receives SMS notification

---

# UC-10 – Manage Farmer Records

## Actor
- Office Staff

## Description
Allows office staff to manage farmer information.

## Preconditions
- Office staff is authenticated

## Main Flow
1. Office staff creates or updates farmer details
2. System validates information
3. System saves farmer record

## Postconditions
- Farmer information is updated successfully