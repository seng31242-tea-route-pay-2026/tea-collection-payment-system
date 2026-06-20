# Mobile Application Wireframes Overview

## Overview

This document provides an overview of the low-fidelity mobile application wireframes created for the TeaRoutePay system.

The mobile application is designed for tea collectors who perform daily tea collection activities in the field. The application supports farmer identification, tea weight recording, offline data storage, and synchronization with the main system.

These wireframes were created to visualize the collector-side user interface before finalizing the system design and implementation.

---

## Objectives

The mobile wireframes were created to:

- Visualize the proposed mobile application interface
- Validate functional requirements
- Improve usability for tea collectors
- Support SDS documentation
- Provide a foundation for future UI development
- Demonstrate the offline-first workflow

---

## Included Wireframes

The following low-fidelity wireframes were prepared.

| Wireframe | Purpose |
|------------|---------|
| QR Scan Screen | Scan farmer QR codes for identification |
| Farmer Details Screen | Display farmer information after QR scan |
| Tea Weight Entry Screen | Record tea collection weight and deductions |
| Offline Saved Records Screen | View records saved offline before synchronization |
| Sync Status Screen | Monitor synchronization progress and status |

---

## QR Scan Screen

### Purpose

Allows tea collectors to identify farmers quickly by scanning the QR code assigned to each farmer.

### Main Components

- Application header
- QR scanner area
- Scan instruction label
- Manual farmer lookup option
- Sync status indicator
- Navigation menu

### Wireframe File

`qr-scan-wireframe.png`

---

## Farmer Details Screen

### Purpose

Displays farmer information after successful QR code scanning or manual lookup.

### Main Components

- Farmer ID
- Farmer Name
- Mobile Number
- Route Information
- Collection summary
- Continue button
- Back button

### Wireframe File

`farmer-details-wireframe.png`

---

## Tea Weight Entry Screen

### Purpose

Allows collectors to record tea leaf weight and apply applicable deductions.

### Main Components

- Farmer information section
- Gross weight input
- Rope sack deduction option
- Water content deduction option
- Deduction summary
- Final net weight display
- Save record button

### Business Rules

- If a rope sack is used, 1 kg is deducted.
- If excess water is detected, 1 kg is deducted.
- Final net weight is calculated automatically.

### Wireframe File

`tea-weight-entry-wireframe.png`

---

## Offline Saved Records Screen

### Purpose

Allows collectors to review collection records saved on the device before synchronization.

### Main Components

- Saved records list
- Farmer name
- Collection date
- Net weight
- Sync pending indicator
- Search functionality
- Record details option

### Wireframe File

`offline-records-wireframe.png`

---

## Sync Status Screen

### Purpose

Provides synchronization information between the mobile application and the main TeaRoutePay system.

### Main Components

- Pending records count
- Successfully synchronized records
- Failed records count
- Sync now button
- Last synchronization time
- Sync progress indicator

### Wireframe File

`sync-status-wireframe.png`

---

## Design Considerations

The wireframes were designed with the following considerations:

- Simple and easy-to-use interface
- Minimal data entry effort
- Support for offline operation
- Fast collection workflow
- Clear visibility of collection data
- Suitable for mobile devices used in field environments

---

## Conclusion

The low-fidelity mobile wireframes provide an initial visualization of the TeaRoutePay collector application. These wireframes support requirement validation, usability review, and future implementation planning before high-fidelity design and development begin.