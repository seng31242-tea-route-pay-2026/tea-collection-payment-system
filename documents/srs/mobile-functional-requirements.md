# Mobile Application Functional Requirements

## Overview

The TeaRoutePay mobile application will be used by tea collectors during daily tea collection routes. The application is designed to replace manual route books and support digital tea collection recording using an offline-first approach.

The mobile application should support QR-based farmer identification, tea leaf weight recording, deduction-related information access, advance payment, offline data storage, and synchronization with the central office system.

This document identifies the functional requirements of the collector-side mobile application.

---

# Purpose of the Mobile Application

The TeaRoutePay mobile application aims to:

- Replace manual route book recording
- Improve collection accuracy
- Reduce duplicate office data entry
- Support offline field operations
- Improve synchronization between field and office systems
- Minimize manual office record entry at the end of the day
- Improve farmer identification and verification

---

# Major Mobile Application Functions

The following major functions are required in the TeaRoutePay mobile application.

| Function | Description |
|---|---|
| User Authentication | Secure collector login |
| QR Code Scanning | Farmer identification using QR codes |
| Farmer Lookup | Search farmers using ID or name |
| Tea Weight Recording | Record tea collection weight |
| Collection Record Management | Create and manage daily collection records |
| Offline Data Storage | Store records locally without internet |
| Route Management | View assigned collection routes |
| Synchronization | Sync records with the office system |
| Validation and Error Handling | Prevent invalid or duplicate records |
| Advance Payment Support | View tea supply history for the previous and current month and provide advance payments to farmers based on the amount of tea supplied  |

---

# Functional Requirements

## FR-01 – User Authentication

### Input
- Username
- Password

### Process
The system validates collector login credentials.

### Output
- Successful login access
- Error message for invalid login

### Validation Rules
- Username cannot be empty
- Password cannot be empty

---

## FR-02 – QR Code Scanning

### Input
- QR code scanned using mobile camera

### Process
The system retrieves farmer information using QR code data.

### Output
- Farmer profile details
- Farmer collection information

### Validation Rules
- QR code must match a registered farmer
- Invalid QR codes should display an error message

---

## FR-03 – Farmer Lookup(If the code is damaged) 

### Input
- Farmer ID
- Farmer name
  
### Process
The system searches and add records.

### Output
- Farmer identification details
- Collection history information

### Validation Rules
- Invalid farmer IDs should generate warnings

---

## FR-04 – Tea Weight Entry

### Input
- Tea leaf weight value

### Process
The system records tea collection weight for the selected farmer.

### Output
- Saved tea collection record

### Validation Rules
- Weight must be numeric
- Negative values are not allowed

---

## FR-05 – Collection Record Management

### Input
- Farmer information
- Tea weight

### Process
The system creates and stores collection records.

### Output
- Updated collection database
- Collection confirmation message

### Validation Rules
- Duplicate records should be prevented
- Required fields must be validated

---

## FR-06 – Offline Data Storage

### Input
- Collection records created without internet access

### Process
The system stores records locally on the device.

### Output
- Offline storage confirmation
- Unsynchronized record tracking

### Validation Rules
- Records must not be lost during offline operation
- Data should remain accessible until synchronization

---

## FR-07 – Route Management

### Input
- Assigned route information

### Process
The system displays daily collection routes for collectors.

### Output
- Route details
- Assigned farmer list

### Validation Rules
- Only assigned routes should be visible

---

## FR-08 – Synchronization

### Input
- Locally stored collection records

### Process
The system synchronizes local records with the central office system when connectivity becomes available.

### Output
- Updated server records
- Synchronization status notifications

### Validation Rules
- Duplicate synchronization must be prevented
- Failed synchronization attempts should be retried safely

---

## FR-09 – Validation and Error Handling

### Input
- User-entered collection data

### Process
The system validates records before saving or synchronization.

### Output
- Error messages
- Validation warnings

### Validation Rules
- Missing fields should generate warnings
- Invalid values should not be saved

---

# QR Scanning and Farmer Lookup Requirements

The system should support:

- QR code scanning using the mobile camera
- Fast farmer identification
- Offline QR verification
- Farmer search using:
  - Farmer ID
  - Farmer name
  - QR code
- Automatic retrieval of farmer details

## Expected Benefits

- Faster collection workflow
- Improved collection accuracy
- Reduced manual identification errors

---

# Offline Storage Requirements

The TeaRoutePay mobile application must support offline-first functionality because collection routes may operate in areas with poor connectivity.

## Required Offline Features

- Local data storage
- Offline collection recording
- Offline farmer lookup
- Offline QR verification
- Local caching of assigned routes
- Unsynchronized record tracking

## Offline Data Handling Requirements

- Records should remain safely stored until synchronization
- No data loss should occur during connectivity interruptions
- Collectors should be able to continue operations offline

---

# End-of-Day Synchronization Requirements

The mobile application should support synchronization between field devices and the office system.

## Synchronization Features

- Automatic synchronization when internet becomes available
- Manual synchronization option
- Synchronization status display
- Conflict handling support
- Duplicate synchronization prevention

## Synchronization Outputs

- Updated office database
- Confirmation messages
- Failed sync notifications if errors occur

---
# Conclusion

The TeaRoutePay mobile application is a critical component of the proposed tea collection management system. The application must support offline-first collection operations, QR-based farmer identification, synchronization, and accurate collection record management to improve operational efficiency and reduce manual processing challenges.
