# QR Code Generation and Scanning Requirements

## Overview

The TeaRoutePay system uses QR codes to identify farmers during tea collection activities. Currently, tea collectors identify farmers manually using route books and farmer record books, which increases the possibility of incorrect farmer selection, duplicate entries, and human errors.

The proposed QR-based identification system improves collection accuracy, reduces manual searching, and speeds up tea collection activities using the TeaRoutePay mobile application.

This document analyses QR code generation requirements, QR scanning requirements, QR storage methods, offline support, damaged QR handling, and fallback identification processes.

---

# Purpose of QR Code Usage

The QR code system is introduced to:

- Improve farmer identification accuracy
- Reduce manual searching during collection
- Reduce typing errors
- Speed up collection operations
- Improve synchronization reliability
- Reduce duplicate collection entries
- Support offline identification processes

---

# QR Code Capacity and Scalability

The proposed QR implementation supports approximately 32 bits of identification capacity.

This allows the system to support approximately:

- Around 100,000 registered farmers
- Unique farmer identification
- Future scalability for additional registrations

The QR implementation is designed to support large-scale tea collection operations efficiently.

---

# Current QR Code Workflow

The TeaRoutePay QR process works as follows:

1. The company places a QR code sticker inside the farmer’s record book.
2. Each farmer receives a unique farmer identification number.
3. Tea collectors use the TeaRoutePay mobile application to scan the QR code.
4. The TeaRoutePay mobile application includes an integrated QR reader.
5. The QR scan retrieves the farmer details from locally stored records.
6. The collector verifies the farmer identity.
7. Tea collection details are recorded.

This process reduces manual searching and improves collection efficiency.

---

# QR Code Data Requirements

The system should maintain the following QR-related information.

| Data Item | Description |
|---|---|
| Farmer ID | Unique farmer identification number |
| Farmer Name | Full farmer name |
| QR Code Hash | Unique QR-related hash value |
| QR Status | Active or inactive status |
| Registration Date | Farmer registration date |
| Route Information | Assigned collection route |
| Mobile Number | Farmer contact number |

---

# QR Data Storage Approach

## Recommended QR Structure

The QR code should contain:

- Farmer unique number
- Hash reference value

Example structure:

```text
FRM-000245-HASH
```

The QR code does not store complete farmer information directly. Instead, it stores a reference value linked to farmer details inside the TeaRoutePay system.

---

# Local Hash Storage

The QR-related hashes are stored locally in the TeaRoutePay mobile application.

This allows:

- Faster farmer lookup
- Offline QR verification
- Reduced internet dependency
- Faster route collection activities

The mobile device can identify farmers without requiring continuous internet connectivity.

---

# QR Code Generation Process

## Step 1 – Farmer Registration

When a new farmer registers:

- Office staff creates a farmer record
- The system generates a unique farmer number

---

## Step 2 – Pre-Printed QR Availability

The company already maintains multiple pre-printed QR codes.

These QR codes are prepared in advance and stored for future farmer registrations.

---

## Step 3 – QR Code Assignment

When assigning a QR code:

- A unique farmer number is added before the QR hash
- The QR code becomes linked to that farmer
- Farmer details are added to the system database

Example:

```text
FRM-000245 + QR-HASH
```

This ensures every farmer receives a unique QR-based identification reference.

---

## Step 4 – QR Sticker Placement

The QR code sticker is attached inside:
- The farmer record book

This allows collectors to scan the QR code easily during collection activities.

---

# QR Generation Functional Requirements

## FR-QR-01 – Unique QR Assignment
The system shall assign a unique QR reference to each farmer.

## FR-QR-02 – Unique Farmer Number Support
The system shall generate a unique farmer identification number.

## FR-QR-03 – QR Hash Management
The system shall manage QR-related hash references securely.

## FR-QR-04 – QR Registration Validation
The system shall prevent duplicate QR assignment.

## FR-QR-05 – QR Replacement Support
The system shall support replacing damaged QR codes.

---

# QR Scanning Process

## Step 1 – Collector Opens Mobile Application

The tea collector opens the TeaRoutePay mobile application.

---

## Step 2 – QR Code Scanning

The collector scans the QR code attached to the farmer record book.

The TeaRoutePay application uses:
- Mobile device camera
- Integrated QR reader

---

## Step 3 – Farmer Identification

After scanning:

- The system retrieves farmer details
- The collector verifies the farmer identity

The lookup process uses:
- Locally stored hash records
- Farmer unique number

---

## Step 4 – Tea Collection Recording

The collector:
- Records tea weight
- Saves collection information

The data is:
- Stored locally if offline
- Synchronized later when internet becomes available

---

# QR Scanning Functional Requirements

## FR-QR-06 – Mobile QR Reader Support
The system shall support QR scanning using the TeaRoutePay mobile application.

## FR-QR-07 – Offline Farmer Identification
The system shall support farmer lookup without internet connectivity.

## FR-QR-08 – Fast Farmer Retrieval
The system shall retrieve farmer details immediately after scanning.

## FR-QR-09 – QR Validation
The system shall validate QR authenticity before displaying farmer data.

## FR-QR-10 – Duplicate Entry Prevention
The system shall reduce duplicate collection records.

## FR-QR-11 – Manual Farmer Identification
The system shall support manual farmer identification if QR scanning fails.


