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



