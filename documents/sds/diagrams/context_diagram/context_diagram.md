# System Context Diagram

This directory contains the System Context Diagram for the TeaRoutePay project, as defined in the system architecture and arequirements documentation.

## Diagram Overview
The context diagram provides a high-level view of the TeaRoutePay system boundary and its interactions with external actors.

### External Actors
1. **Farmer / Supplier**: Provides tea leaves and receives monthly SMS payment notifications.
2. **Collector / Lorry Driver**: Operates the mobile application during field routes to enter weights.
3. **Owner**: Acts as system administrator and office staff; manages system configurations, records, deductions, sets tea rates, approves payments, and views dashboards.
4. **Administrative Developer**: Maintains the system infrastructure, deploys updates, and monitors technical logs and health.
5. **Bank Transfer Service (External)**: Receives approved payment transfer requests and returns statuses.
6. **SMS Gateway (External)**: Receives SMS send requests and returns delivery receipts.


```mermaid
flowchart LR
    %% Core System
    SYSTEM(((TeaRoutePay<br>System)))

    %% External Entities
    FARMER[Farmer / Supplier]
    COLLECTOR[Collector / Lorry Driver]
    OWNER[Owner]
    DEV[Administrative Developer]
    BANK[Bank Transfer Service]
    SMS[SMS Gateway]

    %% Relationships
    FARMER <-->|"Provides tea leaves <br> Receives monthly SMS"| SYSTEM
    COLLECTOR -->|"Operates mobile app <br> Enters weights"| SYSTEM
    OWNER <-->|"Manages system config, records & deductions <br> Sets tea rates & approves payments"| SYSTEM
    DEV <-->|"Deploys updates & maintains system <br> Monitors technical logs & health"| SYSTEM
    SYSTEM <-->|"Payment transfer requests <br> Returns status"| BANK
    SYSTEM <-->|"SMS send requests <br> Returns delivery receipts"| SMS

    %% Styling
    classDef system fill:#2e7d32,stroke:#1b5e20,stroke-width:3px,color:#fff,font-weight:bold;
    classDef actor fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000,font-weight:bold;
    classDef ext_service fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#000,font-weight:bold;
    
    class SYSTEM system;
    class FARMER,COLLECTOR,OWNER,DEV actor;
    class BANK,SMS ext_service;
```
