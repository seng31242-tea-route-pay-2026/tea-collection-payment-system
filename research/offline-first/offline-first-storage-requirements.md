# Offline-First Data Storage Requirements

# 1. Purpose

This document defines the offline-first data storage requirements for the TeaRoutePay mobile system.

Tea collection activities happen in rural areas where internet connectivity may be weak, unstable, or unavailable.  
The mobile application must therefore continue functioning without internet access and synchronize data later when connectivity becomes available.

The goal of this design is to ensure:

- Continuous tea collection operations
- Reliable local data storage
- Safe synchronization to office and cloud systems
- Prevention of data loss during offline usage

---

# 2. System Overview

The TeaRoutePay system uses a multi-layer storage architecture.

The system contains three major layers:

| Layer | Responsibility |
|---|---|
| Mobile Application | Offline field data collection |
| Office Desktop System | Operational processing and validation |
| Cloud System | Centralized long-term storage |

### Databases Used

| System | Database |
|---|---|
| Mobile App | SQLite |
| Office System | PostgreSQL |
| Cloud System | PostgreSQL |

---

# 3. Offline-First Requirements

The mobile application must operate fully offline during field collection activities.

### Required Offline Capabilities

- Farmer identification using QR codes
- Route-based farmer lookup
- Tea collection recording
- Advance payment recording
- New farmer registration
- Local transaction storage
- Temporary sync queue management

### Important Constraints

- Salary processing is NOT handled in the mobile application
- Receipt generation is NOT handled in the mobile application
- Mobile app acts only as a field data collection system
- Internet connection must not be required for core operations

---

# 4. Data Stored Locally (SQLite)

The following data must be available offline inside the mobile application.

| Data Type | Purpose |
|---|---|
| Farmer information | Identify registered farmers |
| QR code mapping | Fast farmer lookup |
| Route information | Identify collection routes |
| Tea collection records | Store collected tea weight |
| Advance payment records | Store temporary payments |
| Newly registered farmers | Temporary local registration |
| Sync queue | Track unsynchronized records |
| Device logs | Debugging and traceability |

---

# 5. Offline Storage Flow

1. Tea collector opens the mobile application
2. Farmer QR code is scanned
3. Data is retrieved from local SQLite database
4. Tea collection data is entered
5. Records are saved locally
6. Records are added to sync queue
7. Synchronization occurs later when connectivity becomes available

---

# 6. Storage Architecture

The mobile application acts as the primary field data collector.

### Storage Flow

- Data is first written to local SQLite storage
- Data remains locally available until synchronization succeeds
- Data may sync to:
  - Office PostgreSQL database
  - Cloud PostgreSQL database
- Office system may later synchronize with cloud storage

The system must continue functioning even if synchronization fails temporarily.

---

# 7. Offline-to-Online Sync Risks

| Risk | Description |
|---|---|
| Duplicate records | Same transaction synced multiple times |
| Missing sync | Records not uploaded before device failure |
| Partial sync failure | Sync interrupted during upload |
| Data inconsistency | Office and mobile data mismatch |
| Timestamp mismatch | Different device times causing ordering issues |
| Device damage | Local data loss before synchronization |
| Network instability | Incomplete synchronization attempts |

---

# 8. Data Conflict Scenarios

The following conflict situations may occur during synchronization.

| Scenario | Example |
|---|---|
| Duplicate submission | Same collection uploaded twice |
| Farmer update conflict | Farmer edited in office and mobile separately |
| Deleted record conflict | Record removed in one system but not another |
| Timestamp conflict | Older data overwriting newer data |
| Partial transaction sync | Some records synced while others fail |

---

# 9. Conflict Handling Strategy

To reduce synchronization conflicts, the system should implement:

- Unique transaction IDs
- Device-generated UUIDs
- Sync status tracking
- Timestamp-based ordering
- Duplicate detection rules
- Audit logging
- Retry mechanisms for failed syncs

### Suggested Sync Status Values

- Pending
- Synced
- Failed
- Retrying

---

# 10. Backup Strategy

The system should support multiple backup layers.

| Layer | Backup Purpose |
|---|---|
| Mobile SQLite | Temporary offline protection |
| Office PostgreSQL | Operational backup |
| Cloud PostgreSQL | Permanent centralized backup |
| Sync logs | Recovery and debugging |

### Additional Recommendations

- Automatic sync retries
- Daily office database backups
- Cloud backup replication
- Device-level encrypted storage

---

# 11. Recommended Offline-First Design Pattern

The recommended architecture pattern is:

> Local-First Storage with Deferred Synchronization

### Why this approach is suitable

- Works in low-connectivity environments
- Reduces operational interruptions
- Prevents field data loss
- Improves reliability for tea collection routes

---

# 12. Conclusion

TeaRoutePay follows an offline-first architecture designed for field operations with unreliable internet connectivity.

The system prioritizes:

- Reliable offline operation
- Safe temporary local storage
- Controlled synchronization
- Conflict prevention
- Data durability

This architecture ensures that tea collection activities can continue without interruption while maintaining accurate synchronization with office and cloud systems.
