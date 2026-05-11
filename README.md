# Tea Collection & Payment System

A system design project for improving tea leaf collection, farmer record management, deduction handling, and monthly payment processing in a tea collection business.

## Project Overview

The current process depends on manual record books and an old Windows-based desktop system. Tea collectors record daily leaf weights during route collection, and office staff later enter the data manually. Monthly payments are then calculated after applying deductions such as loans, fertilizer, and tea-related deductions.

This project designs a modern system that supports offline tea collection, accurate farmer records, payment calculation, reporting, and bank transfer support.

## Main Objectives

- Reduce manual record handling
- Support offline data collection during lorry routes
- Maintain accurate farmer, route, and collection records
- Calculate monthly payments 
- Support both local sync and cloud sync
- Improve office reporting and payment preparation

## Proposed System

The proposed system includes:

- **Collector Mobile App** for tea leaf collection during routes
- **Office Desktop App** for owner and office staff
- **Mobile Local Database** for offline collection records
- **Office Local Database** for local office operation
- **Cloud Server / API** for optional cloud synchronization
- **Cloud Database** for backup and remote access
- **SMS and Bank Transfer Support** for payment communication

Users can choose between **local sync** and **cloud sync** based on operational needs.

## Key Features

- QR code scanning
- Daily tea leaf weight entry
- Route-based collection records
- Farmer profile management
- Monthly tea rate management
- Loan, fertilizer, and tea deduction handling
- Monthly payment calculation
- Receipt and report generation
- Bank transfer support 
- SMS notification support 
- Offline-first data storage
- Local and cloud synchronization

### 1. Data Synchronization Flow

```mermaid
flowchart TD

    subgraph FIELD["Field Collection"]
        FARMER[Farmer]
        MOBILE[Collector Mobile App]
        MOBILE_DB[(Mobile Local Database)]
    end

    subgraph LOCAL["Local Sync Mode"]
        LAN[Local Area Network]
        OFFICE_PC[Main Office Computer]
        OFFICE_DB[(Office Local Database)]
    end

    subgraph CLOUD["Cloud Sync Mode"]
        INTERNET[Internet Connection]
        BACKEND[Backend / API Server]
        CLOUD_DB[(Cloud Database)]
    end

    subgraph OFFICE["Office System"]
        DESKTOP[Office Desktop App]
        OWNER[Owner / Office Staff]
    end

    FARMER -->|QR Scan| MOBILE
    MOBILE -->|Save collection records offline| MOBILE_DB

    MOBILE_DB -->|Local sync selected| LAN
    LAN -->|Transfer data inside local network| OFFICE_PC
    OFFICE_PC -->|Store local records| OFFICE_DB

    OFFICE_DB -->|Load local records| DESKTOP
    DESKTOP -->|Update local records| OFFICE_DB

    MOBILE_DB -->|Cloud sync selected| INTERNET
    INTERNET -->|Upload data| BACKEND
    BACKEND -->|Store synced records| CLOUD_DB
    CLOUD_DB -->|Send updated records| BACKEND
    BACKEND -->|Provide cloud data| DESKTOP

    DESKTOP -->|View records and reports| OWNER

    MOBILE -. Works without internet during collection .-> MOBILE_DB
```
### 2. Office, User Management, Payment, and External Services Flow

```mermaid
flowchart TD

    subgraph OFFICE["Office Management"]
        OWNER[Owner / Office Staff]
        DESKTOP[Office Desktop App]
    end

    subgraph BACKEND_LAYER["Backend Layer"]
        BACKEND[Backend / API Server]
    end

    subgraph DATA["Data Storage"]
        OFFICE_DB[(Office Local Database)]
        CLOUD_DB[(Cloud Database)]
    end

    subgraph SERVICES["External Services"]
        SMS[SMS API / Notification Service]
        BANK[Bank API / Bank Transfer Service]
    end

    OWNER -->|Use system| DESKTOP

    DESKTOP -->|Manage users and roles| BACKEND
    DESKTOP -->|Manage farmer records| BACKEND
    DESKTOP -->|Manage rates and deductions| BACKEND
    DESKTOP -->|Request reports| BACKEND
    DESKTOP -->|Request payment calculation| BACKEND

    BACKEND -->|Read / update local data if local mode is used| OFFICE_DB
    BACKEND -->|Read / update cloud data if cloud mode is used| CLOUD_DB

    BACKEND -->|Return reports and payment summary| DESKTOP

    OWNER -->|Approve payments| DESKTOP
    DESKTOP -->|Submit approved payment request| BACKEND

    BACKEND -->|Send payment SMS| SMS
    BACKEND -->|Process bank transfer| BANK
```
