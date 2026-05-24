# Offline-First Data Storage Requirements

## Project: TeaRoutePay

---

# 1. Purpose

This document defines the offline-first data storage architecture for the TeaRoutePay system.

The system operates in field conditions where internet connectivity is unreliable.  
Therefore, the mobile application must function fully offline and later synchronize data with office and cloud systems.

The mobile app acts as a **bridge system** between farmers, office operations, and cloud storage.

---

# 2. System Overview

The system consists of three layers:

- Mobile Application (Field Layer)
- Office Desktop System (Processing Layer)
- Cloud Database (Central Layer)

### Databases used:

- Mobile: SQLite (local offline DB)
- Office: PostgreSQL (local office DB)
- Cloud: PostgreSQL (central DB)

---

# 3. Mobile Application Role (Critical Behavior)

The mobile system is the **primary field data collector**.

It must support:

- QR-based farmer identification
- Route-based farmer data storage
- Tea collection entry
- Advance payment recording (NOT full salary processing)
- New farmer account creation in the field
- Offline operation without internet dependency
- Temporary sync queue storage

### Important constraints:

- No receipt generation in mobile app
- No salary calculation in mobile app
- Only data collection and temporary records
- Sync happens later when network is available

---

# 4. Data Stored Offline (Mobile SQLite)

| Data Type | Purpose |
|-----------|--------|
| Farmer data (route-based) | Identify farmers during collection |
| QR mapping | Fast farmer lookup |
| Tea collection records | Store collected tea weight |
| Advance payments | Temporary field payments |
| Route data | Define collection path |
| Sync queue | Store unsent records |
| Device logs | Debugging and traceability |

---

# 5. Sync Behavior

Data is always written first to **local SQLite database**.

Synchronization happens in two ways:

- If office network is available → sync to Office DB
- If internet is available → sync directly to Cloud DB
- Office DB later syncs to Cloud DB

Mobile app never depends on real-time internet.

---

# 6. Key System Rule

The mobile application is a:

> **Offline-first bridge system for field data collection**

It ensures:

- Continuous tea collection without interruptions
- Temporary local storage of all operations
- Deferred synchronization to central systems

---

# 7. System Flow Diagram

A[Farmer QR Scan<br>Mobile App] --> B[Local SQLite DB]

B --> C[Tea Collection Entry]
B --> D[Advance Payment Entry]
B --> E[New Farmer Creation]

B --> F[Sync Queue]

F --> G{Connection Available?}

G -->|Office Network| H[Office PostgreSQL DB]
G -->|Internet| I[Cloud PostgreSQL DB]

H --> I
I --> H

---

# 8. Sync Risks

| Risk | Description |
|------|------------|
| Duplicate records | Same data sent multiple times |
| Missing sync | Device loss before upload |
| Data mismatch | Office vs mobile inconsistency |
| Network interruption | Partial sync failure |
| Time mismatch | Different timestamps between systems |

---

# 9. Conflict Handling Strategy

- Use unique IDs for every transaction
- Use timestamps for ordering
- Maintain sync status (pending / synced / failed)
- Detect duplicates at Office/Cloud level
- Keep audit logs for all sync events

---

# 10. Backup Strategy

- Mobile SQLite: temporary offline safety
- Office DB: operational backup
- Cloud DB: permanent storage
- Sync logs: debugging and recovery support

---

# 11. Conclusion

The TeaRoutePay system follows an **offline-first, multi-layer storage architecture** designed to ensure reliable data persistence and synchronization across distributed environments.

The storage design is based on three levels:

- Local mobile storage (SQLite) for offline data capture
- Office storage (PostgreSQL) for processing and validation
- Cloud storage (PostgreSQL) for centralized persistence and backup

This architecture ensures:

- Continuous data capture without network dependency
- Safe temporary storage during offline operations
- Reliable synchronization between local, office, and cloud databases
- Data consistency across all storage layers

Overall, the system prioritizes **data durability, consistency, and sync reliability** in low-connectivity field environments.