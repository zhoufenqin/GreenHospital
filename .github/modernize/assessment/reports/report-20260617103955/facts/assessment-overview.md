# Assessment Overview

This document serves as the navigation entry point for all supplementary assessment documents generated for the GreenHospital (DoctorPatient) application — an ASP.NET MVC 5 hospital management system on .NET Framework 4.5.

## Supplementary Documents

| Document | Description |
|----------|-------------|
| [Architecture Diagram](./architecture-diagram.md) | High-level application architecture diagram and component relationship diagram, including technology stack summary, data storage overview, and key architectural decisions |
| [Dependency Map](./dependency-map.md) | Visual map of all external NuGet package dependencies grouped by functional category (web frameworks, database/ORM, security/auth, frontend UI, utilities), with version and compatibility risk analysis |
| [API & Service Communication Contracts](./api-service-contracts.md) | Full inventory of all 42 HTTP endpoints, DTOs and request/response models, communication patterns, security posture analysis, and a sequence diagram of the primary appointment booking flow |
| [Data Architecture & Persistence Layer](./data-architecture.md) | Entity model ER diagram, database configuration (SQL Server LocalDB + EF6 Code First), key data access patterns, caching strategy, and data classification with PII/PHI sensitivity analysis |
| [Configuration & Externalized Settings Inventory](./configuration-inventory.md) | Complete inventory of all configuration sources (Web.config, OWIN startup, EF migrations), build and runtime profiles, properties with default values, secrets workflow, and framework/runtime version table |
| [Core Business Workflows](./business-workflows.md) | Documentation of five primary business workflows (patient registration, appointment booking, admin configuration, doctor management, user role management), business rules, validation constraints, and authorization model |
