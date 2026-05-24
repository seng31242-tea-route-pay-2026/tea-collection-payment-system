# Non-Functional Requirements (NFRs) Specification

## Overview
This document formalizes the non-functional requirements (NFRs) for the TeaRoutePay system, establishing the strict quality attributes, performance thresholds, security protocols, and operational constraints required for enterprise deployment. These parameters govern the system's architecture to ensure fault tolerance, financial accuracy, and data security in low-connectivity rural environments, aligning with [SENG31242-#19].

---

## 1. Security & Compliance Requirements (AC1)
The system MUST enforce zero-trust security principles, cryptographic data protection, and strict access controls to secure financial ledgers and vendor data.

* **Cryptographic Standards:** * **Data at Rest:** All offline data stored on the mobile edge device MUST be encrypted using industry-standard symmetric encryption to prevent data extraction from lost or compromised devices.
  * **Data in Transit:** All synchronization payloads between the mobile client, desktop system, and cloud backend MUST be transmitted over secure, encrypted transport protocols.
* **Segregation of Duties (Dual Control):** The desktop application MUST strictly enforce a Maker-Checker workflow. The user identity that executes the batch generation function (The Maker) is cryptographically forbidden from executing the authorization function (The Checker) for the same ledger period.
* **Session Management & Expiration:** * Desktop sessions MUST automatically invalidate after 30 minutes of idle inactivity. 
  * Mobile authentication tokens MUST require re-authentication (e.g., via biometric or PIN) every 24 hours to maintain field security.
* **Role-Based Access Control (RBAC):** The system MUST enforce the principle of least privilege. Access to financial reporting, deduction configurations, and manual synchronization overrides is strictly locked to administrative and ownership roles.

## 2. Usability & Environmental Requirements (AC2)
The User Interface (UI) and User Experience (UX) MUST accommodate the physical and environmental realities of field operators and administrative staff.

* **Field Readability (Mobile):** The mobile application UI MUST be designed with high-contrast color palettes and large touch targets to ensure legibility in direct, high-glare sunlight during plantation operations.
* **Localization & Multilingual Support:** All mobile interfaces, desktop dashboards, and automated SMS notifications MUST support English, Sinhala, and Tamil natively, without relying on real-time external translation services.
* **Contextual Offline Indicators:** The mobile application MUST persistently display a clear visual indicator of the current network state (Offline vs. Connected) and the exact count of pending items in the local synchronization queue.
* **Deterministic Error Handling:** System error dialogues MUST translate technical exceptions into actionable business instructions (e.g., prompting the user to re-authenticate rather than displaying raw server error codes).

## 3. Reliability & Availability Requirements (AC3)
The architecture MUST embrace the reality of severe network degradation, ensuring business continuity through robust local-first operations.

* **Absolute Offline Capability:** The mobile application MUST execute its critical path—farmer identification, daily yield entry, and cash advance issuance—with full functionality in air-gapped (zero internet) environments.
* **Stale Edge-Device Lockout:** To prevent the application of obsolete purchasing rates or unauthorized local overrides, the mobile application MUST trigger a hard system lockout if it fails to complete a verified synchronization handshake with the central server for 48 consecutive hours.
* **Graceful Degradation:** The desktop application MUST maintain local operational capabilities even if the secondary cloud backup connection drops, queueing synchronization payloads until external connectivity is restored.

## 4. Performance & Scalability Constraints (AC4)
The system MUST meet the following Service Level Objectives (SLOs) under peak operational loads.

### System Performance Thresholds
* **Local Scan & Retrieval:** The mobile application must recognize and retrieve farmer details from a localized scan in under 500 milliseconds.
* **Synchronization Processing:** The central system must process, validate, and acknowledge a standard daily mobile synchronization payload (approx. 50-100 records) in under 3.0 seconds.
* **Batch Calculation:** Monthly payout batch calculations for the entire active vendor roster must complete in under 10.0 seconds.
* **Asynchronous Execution:** High-latency external operations (e.g., SMS Gateway API calls) MUST be executed asynchronously to guarantee the UI thread never blocks during bulk approvals.

### Backup & Recovery
* **Multi-Tiered Replication:** The system MUST implement a cascading, 3-tier backup architecture: temporary edge queuing (Mobile), daily automated local backups (Office Server), and continuous replication (Cloud).
* **Immutability of Financial Ledgers:** Once a vendor payout transitions to an approved state or a sync payload is committed, the records MUST be locked. Deletion operations are strictly forbidden; corrections MUST be executed via auditable, append-only adjustment entries.

## 5. Data Integrity & Validation Requirements (AC5)
The system MUST enforce strict enterprise data integrity rules to prevent network-induced duplication and mathematical failure states.

* **Distributed Synchronization Idempotency:** The backend MUST reject duplicate payloads. All incoming sync records MUST be validated against a composite primary key structure (e.g., Farmer ID + Date + Collector ID + Timestamp). Duplicate collisions must be silently discarded to clear the mobile queue.
* **Strict Manual Override Precedence:** In the event of a state collision between a mobile sync payload and a local desktop entry, records flagged as manually entered via the desktop SHALL hold absolute, permanent priority.
* **Atomic Transactions:** All financial calculations and database writes MUST be executed within strict transactions ensuring Atomicity, Consistency, Isolation, and Durability (ACID).
* **Negative Carry-Forward Lock (Arrears):** The deduction algorithm MUST contain mathematical circuit breakers. If total aggregated deductions exceed a vendor's gross yield value, the net payout MUST strictly cap at a zero value. The system MUST automatically transfer the unrecovered debt integer to an arrears ledger for the subsequent billing cycle.
