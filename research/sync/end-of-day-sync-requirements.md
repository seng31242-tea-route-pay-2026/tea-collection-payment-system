# End-of-Day Sync Requirements

# 1. Purpose

This document defines the end-of-day synchronization requirements for the TeaRoutePay system.

At the end of collection routes, mobile devices must synchronize locally stored field data with office or cloud systems to avoid manual data re-entry and ensure accurate operational records.

The synchronization process must support:

- Reliable data transfer
- Duplicate prevention
- Failure recovery
- Data consistency across systems

---

# 2. Sync Objectives

The end-of-day sync process is responsible for:

- Uploading tea collection records
- Uploading advance payment records
- Uploading newly registered farmers
- Updating office operational records
- Updating centralized cloud storage
- Clearing successfully synced local queue items

---

# 3. Data That Must Be Synced

The following records must synchronize from the mobile application.

| Data Type | Description |
|---|---|
| Tea collection records | Farmer tea collection details |
| Advance payments | Temporary field payments |
| New farmer registrations | Farmers created in field |
| Route completion records | Route activity summaries |
| Device logs | Operational troubleshooting logs |
| Sync logs | Sync tracking information |

---

# 4. End-of-Day Sync Flow

## Step 1 — Route Completion

Tea collector completes all assigned collection activities.

## Step 2 — Sync Initialization

User manually starts synchronization or automatic sync begins when connection becomes available.

## Step 3 — Local Validation

Application validates:

- Required fields
- Duplicate transaction IDs
- Record completeness

## Step 4 — Data Upload

Records are uploaded to:

- Office PostgreSQL database
- Cloud PostgreSQL database

## Step 5 — Sync Response Handling

System marks records as:

- Pending
- Synced
- Failed
- Retrying

## Step 6 — Sync Completion

Successful records are removed from active sync queue.

---

# 5. Sync Success Scenarios

| Scenario | Expected Result |
|---|---|
| Successful upload | Records marked as synced |
| Office sync successful | Office receives updated data |
| Cloud sync successful | Central storage updated |
| Retry successful | Previously failed records uploaded |

---

# 6. Sync Failure Scenarios

| Failure Scenario | Impact |
|---|---|
| Internet disconnect | Sync interruption |
| Office server unavailable | Office upload failure |
| Cloud server unavailable | Cloud upload failure |
| Duplicate records detected | Record rejection |
| Corrupted local data | Sync validation failure |
| Partial sync failure | Some records remain pending |
| Device shutdown during sync | Incomplete synchronization |

---

# 7. Duplicate Sync Prevention Rules

To prevent duplicate records during synchronization:

- Every transaction must contain a unique ID
- UUIDs should be generated locally on the device
- Synced records must not be re-uploaded
- Server must validate duplicate transaction IDs
- Sync queue must track upload status

### Recommended Sync Status Values

| Status | Meaning |
|---|---|
| Pending | Waiting for upload |
| Synced | Successfully uploaded |
| Failed | Upload failed |
| Retrying | Upload retry in progress |

---

# 8. Data Consistency Requirements

The synchronization process must ensure:

- No data loss during upload
- Correct transaction ordering
- Accurate timestamps
- Reliable retry handling
- Consistent records across all systems

---

# 9. Recommended Sync Strategy

The recommended sync strategy is:

> Store Locally First → Sync Later

### Benefits

- Reliable field operations
- Reduced dependency on internet access
- Better failure recovery
- Improved operational continuity

---

# 10. Basic Retry Strategy

If synchronization fails:

1. Record remains in local sync queue
2. System marks record as failed
3. Application retries sync automatically
4. User may manually retry synchronization
5. Failed sync events are logged for debugging

---

# 11. Security Considerations

The sync process should include:

- Secure API communication
- Authentication validation
- Encrypted local storage
- Audit logging
- Access control for office systems

---

# 12. Conclusion

The TeaRoutePay end-of-day synchronization process is designed to reduce manual office work and ensure accurate transfer of field collection records.

The system prioritizes:

- Reliable synchronization
- Duplicate prevention
- Failure recovery
- Data consistency
- Operational reliability

This approach ensures that tea collection data collected offline can safely synchronize with office and cloud systems once connectivity becomes available.