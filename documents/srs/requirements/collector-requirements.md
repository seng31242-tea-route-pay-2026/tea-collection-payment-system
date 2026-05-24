# Tea Collector Requirements

## Overview

Tea collectors are responsible for collecting tea leaves from farmers during daily collection routes. Currently, tea collection information is manually recorded using lorry route books, which increases the possibility of duplicate entries, delays, and human errors.

The TeaRoutePay mobile application aims to modernize field collection activities by supporting QR-based farmer identification, tea weight recording, offline data storage, and route synchronization.

This document identifies tea collector functional requirements, field activities, mobile application needs, and offline route handling requirements.

---

# Tea Collector Role in the Current Process

Tea collectors currently perform the following activities:

- Travel through assigned collection routes
- Collect tea leaves from farmers
- Verify farmer identity manually
- Measure tea leaf weight
- Record collection information in route books
- Submit collection records to the office
- Support payment-related record verification if required

The current process depends heavily on handwritten route books and manual office data entry.

---

# Current Collector Pain Points

The existing workflow creates several challenges for tea collectors.

## 1. Manual Record Keeping
Collectors manually record all collection details in handwritten route books.

## 2. Time-Consuming Data Recording
Writing collection records manually for each farmer slows down the collection process.

## 3. Human Error Risk
Manual recording may result in:
- Incorrect tea weights
- Missing records
- Duplicate entries
- Incorrect farmer identification

## 4. No Digital Farmer Verification
Collectors currently verify farmers manually without QR support.

## 5. Duplicate Office Data Entry
Collection records must later be re-entered into the office desktop system.

## 6. Poor Connectivity Challenges
Field collection areas may have limited or unstable internet access.

---

# Collector Functional Requirements

## FR-01 – Collector Authentication
The system shall allow tea collectors to securely log into the mobile application.

## FR-02 – QR-Based Farmer Identification
The system shall support QR code scanning for accurate farmer identification.

## FR-03 – Farmer Lookup
The system shall allow collectors to manually search for a farmer when QR code scanning is not possible, using:
- Farmer ID
- Farmer name

## FR-04 – Tea Weight Recording
The system shall allow collectors to record tea leaf weight during collection.

## FR-05 – Collection Record Creation
The system shall create collection records including:
- Farmer information
- Collection date
- Tea weight
- Route information

## FR-06 – Offline Data Storage
The system shall support offline collection recording when internet connectivity is unavailable.

## FR-07 – Route Data Synchronization
The system shall synchronize locally stored route data with the central system when connectivity becomes available.

## FR-08 – Duplicate Entry Prevention
The system shall validate records to reduce duplicate collection entries.

## FR-09 – Daily Route Management
The system shall support viewing and managing assigned collection routes.

## FR-10 – Error Handling and Validation
The system shall validate tea weight entries and required fields before saving records.

---

# QR Scanning Requirements

The TeaRoutePay mobile application should support QR-based farmer identification.

## QR Features Required

- QR code scanning using the mobile device camera
- Fast farmer identification
- Reduction of manual farmer lookup errors
- Support for offline QR verification
- Automatic retrieval of farmer details after scanning

## Expected Benefits

- Faster collection process
- Improved data accuracy
- Reduced duplicate records
- Better farmer identification reliability

---

# Tea Weight Entry Requirements

The mobile application should support accurate tea weight recording.

## Tea Weight Entry Features

- Numeric weight input validation
- Decimal weight support
- Prevention of invalid weight values
- Ability to review entered values before saving
- Weight record editing before synchronization

## Expected Benefits

- Improved collection accuracy
- Reduced calculation errors
- Faster office processing
- Better payment reliability

---

# Offline Route Data Handling Requirements

Tea collection operations may occur in areas with poor internet connectivity. Therefore, offline-first functionality is essential.

## Offline Features Required

- Offline record creation
- Local device storage
- Temporary route data caching
- Offline farmer lookup
- Offline QR code verification
- Delayed synchronization support

## Synchronization Requirements

The system should:
- Automatically sync records when connectivity becomes available
- Prevent duplicate synchronization
- Preserve unsynchronized records safely
- Display synchronization status to collectors

---

# Collector Data Requirements

| Data Item | Description |
|---|---|
| Collector ID | Unique collector identification |
| Assigned Routes | Daily collection routes |
| Farmer Information | Farmer identification details |
| QR Code Data | Farmer QR identification |
| Tea Collection Records | Daily collection history |
| Tea Weight Records | Weight details for each collection |
| Route Sync Status | Synchronization tracking |
| Offline Record Status | Unsynchronized record tracking |

---

# Expected Improvements with TeaRoutePay

The TeaRoutePay system aims to improve tea collection operations through:

- QR-based farmer identification
- Faster collection recording
- Offline-first route management
- Reduced manual paperwork
- Reduced office data entry workload
- Better synchronization support
- Improved collection accuracy
- Better operational efficiency

---

# Conclusion

Tea collectors play a critical role in the tea collection workflow. The current manual process creates operational inefficiencies and increases the risk of human errors. TeaRoutePay aims to modernize route collection activities using mobile technology, offline-first support, and QR-based farmer identification to improve overall efficiency and reliability.
