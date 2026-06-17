# Configuration & Externalized Settings Inventory

The GreenHospital application has a minimal configuration landscape consisting of a single `Web.config` file, two environment-specific transform files (`Web.Debug.config`, `Web.Release.config`), and code-based OWIN/Identity startup configuration — with no external config server, secret store, or feature flag framework.

## Configuration Sources

| Source | Type | Path / Location | Notes |
|--------|------|----------------|-------|
| Web.config | XML application config | `/Web.config` | Primary runtime configuration; connection strings, app settings, Entity Framework, HTTP modules, custom error pages |
| Web.Debug.config | XML transform | `/Web.Debug.config` | Applied on Debug builds; overrides for development environment |
| Web.Release.config | XML transform | `/Web.Release.config` | Applied on Release builds; overrides for production deployment |
| Views/Web.config | XML config | `/Views/Web.config` | Razor view engine configuration; restricts direct access to `.cshtml` files |
| Startup.cs + Startup.Auth.cs | C# code | `/Startup.cs`, `/App_Start/Startup.Auth.cs` | OWIN pipeline startup; configures cookie authentication and external login cookie |
| App_Start/RouteConfig.cs | C# code | `/App_Start/RouteConfig.cs` | URL routing rules |
| App_Start/BundleConfig.cs | C# code | `/App_Start/BundleConfig.cs` | CSS/JS bundle configuration |
| App_Start/FilterConfig.cs | C# code | `/App_Start/FilterConfig.cs` | Global MVC filter registration |
| Migrations/Configuration.cs | C# code | `/Migrations/Configuration.cs` | EF migration configuration; `AutomaticMigrationsEnabled=true`; seed data |

No external config server (Spring Cloud Config, Azure App Configuration), secret store (Key Vault, HashiCorp Vault), or environment variable injection framework is configured.

## Build Profiles

| Profile | Activation | Purpose | Key Changes |
|---------|-----------|---------|------------|
| Debug | Default in Visual Studio; `-p:Configuration=Debug` in MSBuild | Local development | Debug symbols (`full`), no optimization, `DEBUG;TRACE` constants, `DebugType=full` |
| Release | Manual `-p:Configuration=Release`; publish profiles | Production packaging | PDB-only symbols, optimization enabled, `TRACE` constant only, transforms `Web.Release.config` |

Web.config XML transforms (`Web.Debug.config`, `Web.Release.config`) are applied at publish time by MSBuild's Web Publishing Pipeline to produce the final configuration for each target environment.

## Runtime Profiles

| Profile | Activation Method | Config Files | Key Overrides |
|---------|-----------------|-------------|--------------|
| Development | Debug build configuration | `Web.config` + `Web.Debug.config` transform | Debug compilation enabled; transform may override connection strings or error handling |
| Production | Release build/publish | `Web.config` + `Web.Release.config` transform | Optimization enabled; transforms typically disable debug mode and customize error handling |

There are no `appsettings.{Environment}.json` files, `ASPNETCORE_ENVIRONMENT` variable usage, or Spring-style profile-specific config files. The application is .NET Framework 4.5 (not ASP.NET Core), so environment-specific config is handled entirely through Web.config XML transforms.

## Properties Inventory

### Web.config — Connection Strings

| Property Key | Default Value | Profile | Source |
|-------------|--------------|---------|--------|
| DefaultConnection | `Data Source=(LocalDb)\v11.0;AttachDbFilename=|DataDirectory|\Hospital.mdf;Integrated Security=True;MultipleActiveResultSets=true` | All | `Web.config` |

### Web.config — App Settings

| Property Key | Default Value | Profile | Source |
|-------------|--------------|---------|--------|
| webpages:Version | `3.0.0.0` | All | `Web.config` |
| webpages:Enabled | `false` | All | `Web.config` |
| ClientValidationEnabled | `true` | All | `Web.config` |
| UnobtrusiveJavaScriptEnabled | `true` | All | `Web.config` |

### Web.config — System.Web

| Property Key | Default Value | Profile | Source |
|-------------|--------------|---------|--------|
| customErrors mode | `On` | All | `Web.config` |
| customErrors defaultRedirect | `~/Error/General` | All | `Web.config` |
| authentication mode | `None` | All | `Web.config` (OWIN handles auth) |
| compilation debug | `true` | Debug | `Web.config` |
| httpRuntime targetFramework | `4.5` | All | `Web.config` |
| roleManager enabled | `true` | All | `Web.config` |

### Web.config — System.WebServer

| Property Key | Default Value | Profile | Source |
|-------------|--------------|---------|--------|
| httpErrors errorMode | `Detailed` | All | `Web.config` |
| httpErrors 404 path | `/Error/HttpError404` | All | `Web.config` |

### Web.config — Entity Framework

| Property Key | Default Value | Profile | Source |
|-------------|--------------|---------|--------|
| entityFramework defaultConnectionFactory | `System.Data.Entity.Infrastructure.LocalDbConnectionFactory` | All | `Web.config` |
| entityFramework LocalDb parameter | `v11.0` | All | `Web.config` |
| entityFramework provider | `System.Data.Entity.SqlServer.SqlProviderServices` | All | `Web.config` |

### Migrations/Configuration.cs — Seed Data (Runtime Configuration)

| Setting | Value | Notes |
|---------|-------|-------|
| AutomaticMigrationsEnabled | `true` | Schema auto-updated on startup |
| Appointment Duration (ID=1) | `30` (minutes) | Seeded once; editable via Administration UI |
| Working Hours Start (ID=2) | `8` (24h) | Seeded once; editable via Administration UI |
| Working Hours End (ID=3) | `18` (24h) | Seeded once; editable via Administration UI |
| Default Admin Username | `Admin` | Seeded once |
| Default Roles | `Admin`, `Doctor`, `Patient` | Seeded once |

### OWIN / Authentication (Code-Based)

| Setting | Value | Source |
|---------|-------|--------|
| AuthenticationType | `ApplicationCookie` | `Startup.Auth.cs` |
| LoginPath | `/Account/Login` | `Startup.Auth.cs` |
| ExternalSignInCookie | `ExternalCookie` | `Startup.Auth.cs` |
| OWIN Startup Class | `DoctorPatient.Startup` | Assembly attribute in `Startup.cs` |

## Startup Parameters & Resource Requirements

| Service | Runtime Options | Memory | CPU | Instance Count |
|---------|---------------|--------|-----|---------------|
| DoctorPatient Web App | IIS Express on port 49398 (dev); standard IIS for production | Not specified; no Docker/K8s config | Not specified | 1 (no scaling config) |

No JVM startup parameters (Java N/A), no Docker container settings, no Kubernetes resource requests/limits, and no cloud deployment configuration files are present.

## Startup Dependency Chain

The application has a simple single-process startup sequence:

1. **IIS / IIS Express** initializes the ASP.NET application host
2. **OWIN Startup** (`Startup.Configuration`) runs — configures cookie authentication pipeline via `ConfigureAuth(app)`
3. **Global.asax `Application_Start`** runs — registers routes (`RouteConfig`), bundles (`BundleConfig`), filters (`FilterConfig`)
4. **Entity Framework** runs automatic migrations on first database connection — applies pending migrations and executes seed data if the database is new

There are no explicit readiness probes, health checks, Docker Compose `depends_on` conditions, or service-to-service startup ordering requirements. The application depends on SQL Server LocalDB being available on first request; there is no wait mechanism — a failed database connection results in an unhandled exception.

## Secrets & Sensitive Configuration

| Secret Reference | Type | Storage | Notes |
|-----------------|------|---------|-------|
| DefaultConnection (connection string) | SQL Server connection string | `Web.config` (plaintext) | Uses Integrated Security (Windows auth) — no password in connection string |
| Default Admin password (`12345678`) | Application user password | `Migrations/Configuration.cs` (plaintext in source) | Hardcoded seed password; hashed by ASP.NET Identity before storage, but initial value is exposed in source code |
| Social OAuth App Keys/Secrets | OAuth client credentials | Not configured | References to Facebook, Google, Twitter, Microsoft OWIN providers exist in packages but no keys/secrets are configured |

### Secrets Provisioning Workflow

The application has no secrets management workflow. Configuration is stored entirely in `Web.config` and source code:

- **Connection string**: Uses Windows Integrated Security for SQL Server LocalDB — no username/password required, so no credential secret to manage. The connection string is stored in plaintext in `Web.config`.
- **Admin seed password**: The default administrator password (`12345678`) is hardcoded in `Migrations/Configuration.cs`. ASP.NET Identity hashes it with PBKDF2 before storing in the database, but the plaintext value is visible in source control.
- **No secret store integration**: There is no HashiCorp Vault, Azure Key Vault, AWS Secrets Manager, or encrypted property file configured. All configuration is in source-controlled files.
- **Risk**: If social OAuth providers were to be configured, their app keys/secrets would need to be added to `Web.config`, which would expose them in source control if not managed separately.

## Feature Flags

No feature flag framework is configured. The application uses no LaunchDarkly, Unleash, .NET Feature Management, `@ConditionalOnProperty`, or custom toggle mechanism. The `DisableNewAppointments` field on `DoctorModel` functions as a per-doctor operational toggle (not a system-level feature flag) — it is managed through the Administration UI and stored in the database.

## Framework & Runtime Versions

| Component | Version | Source |
|-----------|---------|--------|
| Target Framework | .NET Framework 4.5 | `DoctorPatient.csproj` (TargetFrameworkVersion v4.5) |
| ASP.NET MVC | 5.2.0 | `packages.config` |
| ASP.NET Razor | 3.2.0 | `packages.config` |
| ASP.NET WebPages | 3.2.0 | `packages.config` |
| ASP.NET Web Optimization | 1.1.1 | `packages.config` |
| ASP.NET Identity Core | 2.1.0 | `packages.config` |
| ASP.NET Identity EntityFramework | 2.1.0 | `packages.config` |
| ASP.NET Identity Owin | 2.1.0 | `packages.config` |
| Entity Framework | 6.1.0 | `packages.config` |
| Microsoft.Owin | 2.1.0 | `packages.config` |
| Microsoft.Owin.Host.SystemWeb | 2.0.0 | `packages.config` |
| Microsoft.Owin.Security | 2.1.0 | `packages.config` |
| Bootstrap | 3.0.0 | `packages.config` |
| jQuery | 1.10.2 | `packages.config` |
| Newtonsoft.Json | 5.0.6 | `packages.config` |
| TimePeriodLibrary.NET | 2.0.0 | `packages.config` |
| Build Tool | MSBuild (Visual Studio 2013 ToolsVersion 12.0) | `DoctorPatient.csproj` |
| Web Server (dev) | IIS Express (port 49398) | `DoctorPatient.csproj` project properties |
| Web Server (prod) | IIS (System.Web pipeline) | `Microsoft.Owin.Host.SystemWeb` |
| Package Manager | NuGet (packages.config format) | `packages.config`, `.csproj` hint paths |
