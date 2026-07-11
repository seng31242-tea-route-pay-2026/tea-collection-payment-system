# Software Design Specification (SDS)

This directory contains all SDS source documents and the compiled PDF for the TeaRoutePay system.

## Contents Structure

- `final/` — Compiled PDF (`SDS_TeaRoutePay.pdf`)
- `architecture/` — System architecture and context diagram
- `data-model/` — Entity-Relationship Diagram (ERD) and data dictionary
- `use-cases/` — Use case diagrams and use case descriptions
- `diagrams/` — Activity diagrams (SVG assets and overview)

## Documents

### Architecture
| File | Description |
|---|---|
| `architecture/system-architecture.md` | High-level hybrid architecture specification with mermaid diagrams |
| `architecture/context-diagram.md` | System context diagram showing external actors and system boundaries |

### Data Model
| File | Description |
|---|---|
| `data-model/data-model.md` | Full ERD for both mobile and office/cloud databases, plus data dictionary |

### Use Cases
| File | Description |
|---|---|
| `use-cases/use-case-diagram.md` | Mermaid use case diagrams for Collector, Owner, and Farmer actors |
| `use-cases/use-case-descriptions.md` | Structured UC-01 through UC-10 use case descriptions |

### Diagrams
| File | Description |
|---|---|
| `diagrams/activity-diagrams/activity-diagrams.md` | Overview and embedded SVGs for all 5 activity diagrams |
| `diagrams/activity-diagrams/Activity_diagram_1_daily_collection.svg` | Daily tea leaf collection workflow |
| `diagrams/activity-diagrams/Activity_diagram_2_data_sync.svg` | Data synchronisation (local and cloud) |
| `diagrams/activity-diagrams/Activity_diagram_3_monthly_payment.svg` | Monthly payment calculation and processing |
| `diagrams/activity-diagrams/Activity_diagram_4_deduction_management.svg` | Deduction management (loans and fertilizer) |
| `diagrams/activity-diagrams/Activity_diagram_5_farmer_registration.svg` | Farmer registration and profile management |
