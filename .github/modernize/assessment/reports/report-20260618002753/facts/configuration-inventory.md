# Configuration & Externalized Settings Inventory

This repository has a compact configuration surface centered on classic ASP.NET web configuration, build-time project metadata, and Entity Framework migration settings. There are no separate runtime environment profiles or external secret stores; most behavior comes from `Web.config`, project properties, and seeded database values.

## Configuration Sources

| Source | Type | Path/Location | Notes |
|---|---|---|---|
| `DoctorPatient.csproj` | Build and project metadata | `D:\a\GreenHospital\GreenHospital\DoctorPatient.csproj` | Defines target framework, Debug/Release configs, IIS Express dev URL, package references |
| `packages.config` | Dependency manifest | `D:\a\GreenHospital\GreenHospital\packages.config` | Declares all NuGet packages and versions |
| `Web.config` | Runtime application configuration | `D:\a\GreenHospital\GreenHospital\Web.config` | Connection string, app settings, custom errors, HTTP runtime, binding redirects, EF provider config |
| `Web.Debug.config` | Build transform | `D:\a\GreenHospital\GreenHospital\Web.Debug.config` | Debug-specific web.config transform |
| `Web.Release.config` | Build transform | `D:\a\GreenHospital\GreenHospital\Web.Release.config` | Release-specific web.config transform |
| `Migrations\Configuration.cs` | Programmatic seed configuration | `D:\a\GreenHospital\GreenHospital\Migrations\Configuration.cs` | Seeds admin settings, roles, and default admin account |
| Database `AdministrationModels` rows | Database-backed application settings | SQL data seeded by migration | Stores appointment duration and working-hour settings used at runtime |

## Build Profiles

| Profile | Activation | Purpose | Key Dependencies/Plugins |
|---|---|---|---|
| Debug | Default when no configuration is supplied | Enables symbols, disables optimization, builds to `bin\` | Uses same declared package set; project `debug="true"` in `Web.config` |
| Release | Explicit `Configuration=Release` build | Enables optimization and pdb-only debug info | Uses same declared package set; intended for deployment packaging |

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---|---|---|---|
| Default | Standard ASP.NET startup | `Web.config` | LocalDB connection string, custom errors enabled, Identity and EF provider settings |
| Debug transform | Build/publish transform | `Web.Debug.config` + `Web.config` | Repository contains transform file but no separate environment-specific runtime model |
| Release transform | Build/publish transform | `Web.Release.config` + `Web.config` | Repository contains transform file but no separate environment-specific runtime model |

## Properties Inventory

### Web and MVC

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `webpages:Version` | `3.0.0.0` | Default | `Web.config` |
| `webpages:Enabled` | `false` | Default | `Web.config` |
| `ClientValidationEnabled` | `true` | Default | `Web.config` |
| `UnobtrusiveJavaScriptEnabled` | `true` | Default | `Web.config` |
| `system.web/customErrors@mode` | `On` | Default | `Web.config` |
| `system.web/compilation@debug` | `true` | Default | `Web.config` |
| `system.web/compilation@targetFramework` | `4.5` | Default | `Web.config` |
| `system.web/httpRuntime@targetFramework` | `4.5` | Default | `Web.config` |

### Database and Entity Framework

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `connectionStrings:DefaultConnection` | `[Integrated Security LocalDB connection]` | Default | `Web.config` |
| `entityFramework/defaultConnectionFactory` | `LocalDbConnectionFactory` with parameter `v11.0` | Default | `Web.config` |
| `entityFramework/provider:System.Data.SqlClient` | `EntityFramework.SqlServer.SqlProviderServices` | Default | `Web.config` |
| `AutomaticMigrationsEnabled` | `true` | Default | `Migrations\Configuration.cs` |
| `AdministrationModel[1]` | `30` minutes | Database seed | `Migrations\Configuration.cs` |
| `AdministrationModel[2]` | `8` | Database seed | `Migrations\Configuration.cs` |
| `AdministrationModel[3]` | `18` | Database seed | `Migrations\Configuration.cs` |

### Hosting and Errors

| Property Key | Default | Profiles | Source |
|---|---|---|---|
| `httpErrors@errorMode` | `Detailed` | Default | `Web.config` |
| `httpErrors:404/path` | `/Error/HttpError404` | Default | `Web.config` |
| `IISUrl` | `http://localhost:49398/` | Debug project metadata | `DoctorPatient.csproj` |
| `UseIISExpress` | `true` | Debug project metadata | `DoctorPatient.csproj` |

## Startup Parameters & Resource Requirements

| Service | JVM/Runtime Options | Memory | Instance Count |
|---|---|---|---|
| DoctorPatient | None explicitly configured in repository | Not specified | Not specified |

No command-line startup parameters, heap settings, container resources, or horizontal scaling settings are defined in the repository.

## Startup Dependency Chain

1. `DoctorPatient` web application starts under IIS Express or IIS.
2. OWIN authentication middleware is configured from `Startup.Auth.cs`.
3. Entity Framework initializes `HospitalDbContext` when first used.
4. The application depends on the LocalDB database file and EF migrations/seed data being available before identity, appointment scheduling, and admin settings can function correctly.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage (masked) |
|---|---|---|
| `DefaultConnection` | Database connection string | LocalDB integrated-security connection, no password present in file |
| Seeded admin password in migration | Default account credential | Source code literal `[MASKED]` in `Migrations\Configuration.cs` |

### Secrets Provisioning Workflow

The repository does not use an external secret manager, environment-variable secret injection, or managed identity flow. Sensitive configuration is either absent from files because LocalDB uses integrated security, or embedded directly in source-backed migration seeding for the bootstrap administrator account, which means secret provisioning today is manual and code-driven rather than environment-driven.

## Feature Flags

| Flag Name | Default | Controlled By |
|---|---|---|
| None detected | n/a | n/a |

## Framework & Runtime Versions

| Component | Version | Source |
|---|---:|---|
| .NET Framework target | 4.5 | `DoctorPatient.csproj` |
| ASP.NET MVC | 5.2.0 | `packages.config` |
| ASP.NET Razor | 3.2.0 | `packages.config` |
| ASP.NET WebPages | 3.2.0 | `packages.config` |
| Entity Framework | 6.1.0 | `packages.config` |
| ASP.NET Identity Core | 2.1.0 | `packages.config` |
| Microsoft.Owin | 2.1.0 | `packages.config` |
| Newtonsoft.Json | 5.0.6 | `packages.config` |
| bootstrap | 3.0.0 | `packages.config` |
| jQuery | 1.10.2 | `packages.config` |
| Project tools version | 12.0 | `DoctorPatient.csproj` |
