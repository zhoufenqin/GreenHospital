# DoctorPatient

## Summary

| Metric | Value |
|--------|-------|
| Total Issues | 24 |
| Mandatory Blockers | 13 |
| Potential Issues | 5 |

## Component Information

| Property | Value |
|----------|-------|
| Language | C# |
| Frameworks | .NETFramework,Version=v4.5 |
| Build tools | MSBuild |

## Cloud Readiness Issues

| Issue Name | Criticality | Story Points | Occurrences |
|------------|-------------|--------------|-------------|
| Windows authentication detected | Mandatory | 3 | [1](#Windows_authentication_detected) |
| Old .NET Framework dependency detected | Potential | 3 | [1](#Old_NET_Framework_dependency_detected) |
| SQL database connection detected | Potential | 3 | [1](#SQL_database_connection_detected) |
| Hardcoded sensitive data detected | Optional | 3 | [14](#Hardcoded_sensitive_data_detected) |
| Static content detected | Optional | 3 | [1](#Static_content_detected) |
| System.Data.SqlClient dependency detected | Optional | 3 | [1](#System_Data_SqlClient_dependency_detected) |
| Connection strings without configuration builders detected | Optional | 3 | [1](#Connection_strings_without_configuration_builders_detected) |

### Issue Details

<details id="Windows_authentication_detected">
<summary><b>Windows authentication detected</b> — affected files</summary>

- `Web.config`

</details>

<details id="Old_NET_Framework_dependency_detected">
<summary><b>Old .NET Framework dependency detected</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="SQL_database_connection_detected">
<summary><b>SQL database connection detected</b> — affected files</summary>

- `Web.config`

</details>

<details id="Hardcoded_sensitive_data_detected">
<summary><b>Hardcoded sensitive data detected</b> — affected files</summary>

- `Controllers\AccountController.cs (line 137)`
- `Controllers\AccountController.cs (line 55)`
- `Controllers\AccountController.cs (line 101)`
- `Controllers\AccountController.cs (line 102)`
- `ViewModels\AccountViewModels.cs (line 22)`
- `ViewModels\AccountViewModels.cs (line 54)`
- `ViewModels\AccountViewModels.cs (line 12)`
- `ViewModels\AccountViewModels.cs (line 18)`
- `ViewModels\AccountViewModels.cs (line 23)`
- `ViewModels\AccountViewModels.cs (line 35)`
- `ViewModels\AccountViewModels.cs (line 50)`
- `ViewModels\AccountViewModels.cs (line 55)`
- `ViewModels\AccountViewModels.cs (line 23)`
- `ViewModels\AccountViewModels.cs (line 55)`

</details>

<details id="Static_content_detected">
<summary><b>Static content detected</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="System_Data_SqlClient_dependency_detected">
<summary><b>System.Data.SqlClient dependency detected</b> — affected files</summary>

- `Web.config`

</details>

<details id="Connection_strings_without_configuration_builders_detected">
<summary><b>Connection strings without configuration builders detected</b> — affected files</summary>

- `Web.config`

</details>

## DotNET Upgrade Issues [View Details](scenarios/dotnet-version-upgrade/assessment.md)

| Issue Category | Criticality | Story Points | Occurrences |
|----------------|-------------|--------------|-------------|
| Binary incompatible for selected .NET version | Mandatory | 1 | [625](#Binary_incompatible_for_selected_NET_version) |
| NuGet package is incompatible | Mandatory | 1 | [15](#NuGet_package_is_incompatible) |
| System.Web.Optimization bundling and minification is not supported in .NET Core and should be replaced with actual html tags pointing to content files | Mandatory | 1 | [11](#System_Web_Optimization_bundling_and_minification_is_not_supported_in_NET_Core_and_should_be_replaced_with_actual_html_tags_pointing_to_content_files) |
| NuGet package functionality is included with framework reference | Mandatory | 1 | [4](#NuGet_package_functionality_is_included_with_framework_reference) |
| GlobalFilterCollection is not supported in .NET Core and needs to be converted to the corresponding middleware registrations on the application object | Mandatory | 1 | [2](#GlobalFilterCollection_is_not_supported_in_NET_Core_and_needs_to_be_converted_to_the_corresponding_middleware_registrations_on_the_application_object) |
| Routes registration via RouteCollection is not supported in .NET Core and needs to be converted to the route mappings on the application object | Mandatory | 1 | [2](#Routes_registration_via_RouteCollection_is_not_supported_in_NET_Core_and_needs_to_be_converted_to_the_route_mappings_on_the_application_object) |
| Convert from Owin to native ASP.NET Core middleware | Mandatory | 1 | [2](#Convert_from_Owin_to_native_ASP_NET_Core_middleware) |
| Project file needs to be converted to SDK-style | Mandatory | 1 | [1](#Project_file_needs_to_be_converted_to_SDK-style) |
| Project's target framework(s) needs to be changed | Mandatory | 1 | [1](#Project_s_target_framework_s_needs_to_be_changed) |
| Default ASP.NET identity should be converted to AspNetCore identity | Mandatory | 1 | [1](#Default_ASP_NET_identity_should_be_converted_to_AspNetCore_identity) |
| Convert application initialization code from Global.asax.cs to .NET Core and clean up Global.asax.cs | Mandatory | 1 | [1](#Convert_application_initialization_code_from_Global_asax_cs_to_NET_Core_and_clean_up_Global_asax_cs) |
| ASP.NET Framework (System.Web) | Mandatory | 4 | 0 |
| Source incompatible for selected .NET version | Potential | 1 | [27](#Source_incompatible_for_selected_NET_version) |
| NuGet package upgrade is recommended | Potential | 1 | [3](#NuGet_package_upgrade_is_recommended) |
| Binding redirect forces version downgrade | Potential | 1 | [1](#Binding_redirect_forces_version_downgrade) |
| NuGet package is deprecated | Optional | 1 | [11](#NuGet_package_is_deprecated) |
| NuGet package contains security vulnerability | Optional | 1 | [7](#NuGet_package_contains_security_vulnerability) |

### Issue Details

<details id="Binary_incompatible_for_selected_NET_version">
<summary><b>Binary incompatible for selected .NET version</b> — affected files</summary>

- `Models\IdentityModel.cs (line 8, col 35)`
- `ViewModels\AccountViewModels.cs (line 199, col 8)`
- `Models\IdentityManager.cs (line 62, col 12)`
- `Models\IdentityManager.cs (line 54, col 16)`
- `Models\IdentityManager.cs (line 48, col 12)`
- `Models\IdentityManager.cs (line 40, col 12)`
- `Models\IdentityManager.cs (line 39, col 12)`
- `Models\IdentityManager.cs (line 31, col 12)`
- `Models\IdentityManager.cs (line 30, col 12)`
- `Models\IdentityManager.cs (line 22, col 12)`
- `Models\IdentityManager.cs (line 21, col 12)`
- `Models\IdentityManager.cs (line 13, col 12)`
- `Models\BuisnessLogic.cs (line 107, col 12)`
- `Models\BuisnessLogic.cs (line 97, col 20)`
- `Infrastructure\HospitalDbContext.cs (line 8, col 35)`
- `Infrastructure\HospitalDbContext.cs (line 6, col 37)`
- `Controllers\RegisteredUsersController.cs (line 121, col 8)`
- `Controllers\RegisteredUsersController.cs (line 123, col 9)`
- `Controllers\RegisteredUsersController.cs (line 122, col 9)`
- `Controllers\RegisteredUsersController.cs (line 121, col 9)`
- `Controllers\RegisteredUsersController.cs (line 141, col 12)`
- `Controllers\RegisteredUsersController.cs (line 139, col 16)`
- `Controllers\RegisteredUsersController.cs (line 126, col 12)`
- `Controllers\RegisteredUsersController.cs (line 112, col 8)`
- `Controllers\RegisteredUsersController.cs (line 112, col 9)`
- `Controllers\RegisteredUsersController.cs (line 118, col 12)`
- `Controllers\RegisteredUsersController.cs (line 108, col 12)`
- `Controllers\RegisteredUsersController.cs (line 90, col 8)`
- `Controllers\RegisteredUsersController.cs (line 92, col 9)`
- `Controllers\RegisteredUsersController.cs (line 91, col 9)`
- `Controllers\RegisteredUsersController.cs (line 90, col 19)`
- `Controllers\RegisteredUsersController.cs (line 90, col 9)`
- `Controllers\RegisteredUsersController.cs (line 99, col 12)`
- `Controllers\RegisteredUsersController.cs (line 97, col 12)`
- `Controllers\RegisteredUsersController.cs (line 77, col 8)`
- `Controllers\RegisteredUsersController.cs (line 77, col 9)`
- `Controllers\RegisteredUsersController.cs (line 87, col 12)`
- `Controllers\RegisteredUsersController.cs (line 85, col 16)`
- `Controllers\RegisteredUsersController.cs (line 53, col 9)`
- `Controllers\RegisteredUsersController.cs (line 52, col 9)`
- `Controllers\RegisteredUsersController.cs (line 51, col 9)`
- `Controllers\RegisteredUsersController.cs (line 73, col 12)`
- `Controllers\RegisteredUsersController.cs (line 69, col 16)`
- `Controllers\RegisteredUsersController.cs (line 56, col 12)`
- `Controllers\RegisteredUsersController.cs (line 40, col 8)`
- `Controllers\RegisteredUsersController.cs (line 40, col 9)`
- `Controllers\RegisteredUsersController.cs (line 47, col 12)`
- `Controllers\RegisteredUsersController.cs (line 46, col 12)`
- `Controllers\RegisteredUsersController.cs (line 28, col 8)`
- `Controllers\RegisteredUsersController.cs (line 28, col 9)`
- `Controllers\RegisteredUsersController.cs (line 36, col 12)`
- `Controllers\RegisteredUsersController.cs (line 31, col 12)`
- `Controllers\RegisteredUsersController.cs (line 14, col 8)`
- `Controllers\RegisteredUsersController.cs (line 14, col 9)`
- `Controllers\RegisteredUsersController.cs (line 24, col 12)`
- `Controllers\RegisteredUsersController.cs (line 9, col 45)`
- `Controllers\HomeController.cs (line 38, col 12)`
- `Controllers\HomeController.cs (line 28, col 8)`
- `Controllers\HomeController.cs (line 32, col 12)`
- `Controllers\HomeController.cs (line 30, col 12)`
- `Controllers\HomeController.cs (line 16, col 8)`
- `Controllers\HomeController.cs (line 25, col 12)`
- `Controllers\HomeController.cs (line 11, col 8)`
- `Controllers\HomeController.cs (line 13, col 12)`
- `Controllers\HomeController.cs (line 7, col 34)`
- `Controllers\ErrorController.cs (line 28, col 8)`
- `Controllers\ErrorController.cs (line 31, col 12)`
- `Controllers\ErrorController.cs (line 23, col 8)`
- `Controllers\ErrorController.cs (line 25, col 12)`
- `Controllers\ErrorController.cs (line 17, col 8)`
- `Controllers\ErrorController.cs (line 20, col 12)`
- `Controllers\ErrorController.cs (line 11, col 8)`
- `Controllers\ErrorController.cs (line 14, col 12)`
- `Controllers\ErrorController.cs (line 8, col 35)`
- `Controllers\AdministrationController.cs (line 9, col 5)`
- `Controllers\AdministrationController.cs (line 57, col 12)`
- `Controllers\AdministrationController.cs (line 40, col 34)`
- `Controllers\AdministrationController.cs (line 38, col 8)`
- `Controllers\AdministrationController.cs (line 39, col 9)`
- `Controllers\AdministrationController.cs (line 38, col 9)`
- `Controllers\AdministrationController.cs (line 48, col 12)`
- `Controllers\AdministrationController.cs (line 46, col 16)`
- `Controllers\AdministrationController.cs (line 42, col 12)`
- `Controllers\AdministrationController.cs (line 21, col 8)`
- `Controllers\AdministrationController.cs (line 32, col 12)`
- `Controllers\AdministrationController.cs (line 30, col 16)`
- `Controllers\AdministrationController.cs (line 25, col 16)`
- `Controllers\AdministrationController.cs (line 15, col 8)`
- `Controllers\AdministrationController.cs (line 17, col 12)`
- `Controllers\AdministrationController.cs (line 10, col 44)`
- `Controllers\DoctorController.cs (line 220, col 12)`
- `Controllers\DoctorController.cs (line 203, col 8)`
- `Controllers\DoctorController.cs (line 205, col 9)`
- `Controllers\DoctorController.cs (line 204, col 19)`
- `Controllers\DoctorController.cs (line 204, col 9)`
- `Controllers\DoctorController.cs (line 203, col 9)`
- `Controllers\DoctorController.cs (line 211, col 12)`
- `Controllers\DoctorController.cs (line 187, col 8)`
- `Controllers\DoctorController.cs (line 187, col 9)`
- `Controllers\DoctorController.cs (line 199, col 12)`
- `Controllers\DoctorController.cs (line 197, col 16)`
- `Controllers\DoctorController.cs (line 192, col 16)`
- `Controllers\DoctorController.cs (line 175, col 34)`
- `Controllers\DoctorController.cs (line 172, col 8)`
- `Controllers\DoctorController.cs (line 174, col 9)`
- `Controllers\DoctorController.cs (line 173, col 9)`
- `Controllers\DoctorController.cs (line 172, col 9)`
- `Controllers\DoctorController.cs (line 183, col 12)`
- `Controllers\DoctorController.cs (line 181, col 16)`
- `Controllers\DoctorController.cs (line 177, col 12)`
- `Controllers\DoctorController.cs (line 154, col 8)`
- `Controllers\DoctorController.cs (line 154, col 9)`
- `Controllers\DoctorController.cs (line 166, col 12)`
- `Controllers\DoctorController.cs (line 164, col 16)`
- `Controllers\DoctorController.cs (line 159, col 16)`
- `Controllers\DoctorController.cs (line 141, col 36)`
- `Controllers\DoctorController.cs (line 138, col 8)`
- `Controllers\DoctorController.cs (line 140, col 9)`
- `Controllers\DoctorController.cs (line 139, col 9)`
- `Controllers\DoctorController.cs (line 138, col 9)`
- `Controllers\DoctorController.cs (line 150, col 12)`
- `Controllers\DoctorController.cs (line 147, col 16)`
- `Controllers\DoctorController.cs (line 143, col 12)`
- `Controllers\DoctorController.cs (line 129, col 8)`
- `Controllers\DoctorController.cs (line 129, col 9)`
- `Controllers\DoctorController.cs (line 132, col 12)`
- `Controllers\DoctorController.cs (line 95, col 8)`
- `Controllers\DoctorController.cs (line 95, col 9)`
- `Controllers\DoctorController.cs (line 124, col 16)`
- `Controllers\DoctorController.cs (line 121, col 20)`
- `Controllers\DoctorController.cs (line 116, col 20)`
- `Controllers\DoctorController.cs (line 114, col 16)`
- `Controllers\DoctorController.cs (line 110, col 16)`
- `Controllers\DoctorController.cs (line 107, col 20)`
- `Controllers\DoctorController.cs (line 57, col 8)`
- `Controllers\DoctorController.cs (line 57, col 9)`
- `Controllers\DoctorController.cs (line 90, col 16)`
- `Controllers\DoctorController.cs (line 87, col 20)`
- `Controllers\DoctorController.cs (line 82, col 20)`
- `Controllers\DoctorController.cs (line 80, col 16)`
- `Controllers\DoctorController.cs (line 76, col 16)`
- `Controllers\DoctorController.cs (line 69, col 20)`
- `Controllers\DoctorController.cs (line 40, col 8)`
- `Controllers\DoctorController.cs (line 53, col 12)`
- `Controllers\DoctorController.cs (line 52, col 12)`
- `Controllers\DoctorController.cs (line 51, col 12)`
- `Controllers\DoctorController.cs (line 45, col 16)`
- `Controllers\DoctorController.cs (line 16, col 8)`
- `Controllers\DoctorController.cs (line 36, col 12)`
- `Controllers\DoctorController.cs (line 22, col 12)`
- `Controllers\DoctorController.cs (line 11, col 36)`
- `Controllers\AppointmentController.cs (line 203, col 8)`
- `Controllers\AppointmentController.cs (line 203, col 9)`
- `Controllers\AppointmentController.cs (line 207, col 12)`
- `Controllers\AppointmentController.cs (line 199, col 12)`
- `Controllers\AppointmentController.cs (line 175, col 8)`
- `Controllers\AppointmentController.cs (line 177, col 9)`
- `Controllers\AppointmentController.cs (line 176, col 9)`
- `Controllers\AppointmentController.cs (line 175, col 19)`
- `Controllers\AppointmentController.cs (line 175, col 9)`
- `Controllers\AppointmentController.cs (line 190, col 16)`
- `Controllers\AppointmentController.cs (line 188, col 16)`
- `Controllers\AppointmentController.cs (line 187, col 17)`
- `Controllers\AppointmentController.cs (line 186, col 16)`
- `Controllers\AppointmentController.cs (line 185, col 17)`
- `Controllers\AppointmentController.cs (line 184, col 16)`
- `Controllers\AppointmentController.cs (line 183, col 12)`
- `Controllers\AppointmentController.cs (line 159, col 8)`
- `Controllers\AppointmentController.cs (line 159, col 9)`
- `Controllers\AppointmentController.cs (line 171, col 12)`
- `Controllers\AppointmentController.cs (line 169, col 16)`
- `Controllers\AppointmentController.cs (line 164, col 16)`
- `Controllers\AppointmentController.cs (line 124, col 34)`
- `Controllers\AppointmentController.cs (line 121, col 8)`
- `Controllers\AppointmentController.cs (line 123, col 9)`
- `Controllers\AppointmentController.cs (line 122, col 9)`
- `Controllers\AppointmentController.cs (line 121, col 9)`
- `Controllers\AppointmentController.cs (line 155, col 12)`
- `Controllers\AppointmentController.cs (line 154, col 12)`
- `Controllers\AppointmentController.cs (line 153, col 12)`
- `Controllers\AppointmentController.cs (line 150, col 16)`
- `Controllers\AppointmentController.cs (line 148, col 20)`
- `Controllers\AppointmentController.cs (line 146, col 16)`
- `Controllers\AppointmentController.cs (line 141, col 12)`
- `Controllers\AppointmentController.cs (line 137, col 20)`
- `Controllers\AppointmentController.cs (line 128, col 16)`
- `Controllers\AppointmentController.cs (line 100, col 8)`
- `Controllers\AppointmentController.cs (line 100, col 9)`
- `Controllers\AppointmentController.cs (line 115, col 12)`
- `Controllers\AppointmentController.cs (line 114, col 12)`
- `Controllers\AppointmentController.cs (line 113, col 12)`
- `Controllers\AppointmentController.cs (line 112, col 12)`
- `Controllers\AppointmentController.cs (line 110, col 16)`
- `Controllers\AppointmentController.cs (line 105, col 16)`
- `Controllers\AppointmentController.cs (line 60, col 36)`
- `Controllers\AppointmentController.cs (line 57, col 8)`
- `Controllers\AppointmentController.cs (line 59, col 9)`
- `Controllers\AppointmentController.cs (line 58, col 9)`
- `Controllers\AppointmentController.cs (line 57, col 9)`
- `Controllers\AppointmentController.cs (line 96, col 12)`
- `Controllers\AppointmentController.cs (line 95, col 12)`
- `Controllers\AppointmentController.cs (line 94, col 12)`
- `Controllers\AppointmentController.cs (line 90, col 16)`
- `Controllers\AppointmentController.cs (line 86, col 12)`
- `Controllers\AppointmentController.cs (line 82, col 20)`
- `Controllers\AppointmentController.cs (line 77, col 20)`
- `Controllers\AppointmentController.cs (line 67, col 16)`
- `Controllers\AppointmentController.cs (line 63, col 12)`
- `Controllers\AppointmentController.cs (line 42, col 8)`
- `Controllers\AppointmentController.cs (line 42, col 9)`
- `Controllers\AppointmentController.cs (line 51, col 12)`
- `Controllers\AppointmentController.cs (line 47, col 12)`
- `Controllers\AppointmentController.cs (line 46, col 12)`
- `Controllers\AppointmentController.cs (line 45, col 12)`
- `Controllers\AppointmentController.cs (line 26, col 8)`
- `Controllers\AppointmentController.cs (line 26, col 9)`
- `Controllers\AppointmentController.cs (line 38, col 12)`
- `Controllers\AppointmentController.cs (line 36, col 16)`
- `Controllers\AppointmentController.cs (line 31, col 16)`
- `Controllers\AppointmentController.cs (line 18, col 8)`
- `Controllers\AppointmentController.cs (line 18, col 9)`
- `Controllers\AppointmentController.cs (line 22, col 12)`
- `Controllers\AppointmentController.cs (line 13, col 41)`
- `Controllers\AccountController.cs (line 11, col 5)`
- `Controllers\AccountController.cs (line 223, col 8)`
- `Controllers\AccountController.cs (line 231, col 16)`
- `Controllers\AccountController.cs (line 227, col 16)`
- `Controllers\AccountController.cs (line 225, col 12)`
- `Controllers\AccountController.cs (line 207, col 12)`
- `Controllers\AccountController.cs (line 197, col 8)`
- `Controllers\AccountController.cs (line 201, col 16)`
- `Controllers\AccountController.cs (line 199, col 12)`
- `Controllers\AccountController.cs (line 193, col 12)`
- `Controllers\AccountController.cs (line 192, col 12)`
- `Controllers\AccountController.cs (line 186, col 16)`
- `Controllers\AccountController.cs (line 177, col 12)`
- `Controllers\AccountController.cs (line 162, col 8)`
- `Controllers\AccountController.cs (line 163, col 9)`
- `Controllers\AccountController.cs (line 162, col 9)`
- `Controllers\AccountController.cs (line 167, col 12)`
- `Controllers\AccountController.cs (line 113, col 9)`
- `Controllers\AccountController.cs (line 112, col 9)`
- `Controllers\AccountController.cs (line 158, col 12)`
- `Controllers\AccountController.cs (line 148, col 24)`
- `Controllers\AccountController.cs (line 146, col 20)`
- `Controllers\AccountController.cs (line 145, col 20)`
- `Controllers\AccountController.cs (line 143, col 16)`
- `Controllers\AccountController.cs (line 140, col 20)`
- `Controllers\AccountController.cs (line 137, col 16)`
- `Controllers\AccountController.cs (line 126, col 24)`
- `Controllers\AccountController.cs (line 124, col 20)`
- `Controllers\AccountController.cs (line 123, col 20)`
- `Controllers\AccountController.cs (line 121, col 16)`
- `Controllers\AccountController.cs (line 118, col 12)`
- `Controllers\AccountController.cs (line 117, col 12)`
- `Controllers\AccountController.cs (line 98, col 8)`
- `Controllers\AccountController.cs (line 108, col 12)`
- `Controllers\AccountController.cs (line 107, col 12)`
- `Controllers\AccountController.cs (line 106, col 12)`
- `Controllers\AccountController.cs (line 100, col 12)`
- `Controllers\AccountController.cs (line 73, col 9)`
- `Controllers\AccountController.cs (line 72, col 9)`
- `Controllers\AccountController.cs (line 71, col 9)`
- `Controllers\AccountController.cs (line 94, col 12)`
- `Controllers\AccountController.cs (line 85, col 20)`
- `Controllers\AccountController.cs (line 80, col 16)`
- `Controllers\AccountController.cs (line 76, col 12)`
- `Controllers\AccountController.cs (line 64, col 8)`
- `Controllers\AccountController.cs (line 64, col 9)`
- `Controllers\AccountController.cs (line 67, col 12)`
- `Controllers\AccountController.cs (line 37, col 9)`
- `Controllers\AccountController.cs (line 36, col 9)`
- `Controllers\AccountController.cs (line 35, col 9)`
- `Controllers\AccountController.cs (line 60, col 12)`
- `Controllers\AccountController.cs (line 55, col 20)`
- `Controllers\AccountController.cs (line 50, col 28)`
- `Controllers\AccountController.cs (line 45, col 24)`
- `Controllers\AccountController.cs (line 40, col 12)`
- `Controllers\AccountController.cs (line 27, col 8)`
- `Controllers\AccountController.cs (line 27, col 9)`
- `Controllers\AccountController.cs (line 31, col 12)`
- `Controllers\AccountController.cs (line 30, col 12)`
- `Controllers\AccountController.cs (line 19, col 8)`
- `Controllers\AccountController.cs (line 12, col 37)`
- `Global.asax.cs (line 65, col 12)`
- `Global.asax.cs (line 58, col 20)`
- `Global.asax.cs (line 57, col 20)`
- `Global.asax.cs (line 53, col 20)`
- `Global.asax.cs (line 49, col 20)`
- `Global.asax.cs (line 45, col 20)`
- `Global.asax.cs (line 40, col 12)`
- `Global.asax.cs (line 39, col 12)`
- `Global.asax.cs (line 38, col 12)`
- `Global.asax.cs (line 27, col 12)`
- `Global.asax.cs (line 21, col 12)`
- `Global.asax.cs (line 16, col 12)`
- `Global.asax.cs (line 15, col 12)`
- `Global.asax.cs (line 14, col 12)`
- `Global.asax.cs (line 13, col 12)`
- `App_Start\Startup.Auth.cs (line 19, col 12)`
- `App_Start\Startup.Auth.cs (line 13, col 12)`
- `App_Start\RouteConfig.cs (line 11, col 8)`
- `App_Start\RouteConfig.cs (line 15, col 12)`
- `App_Start\RouteConfig.cs (line 13, col 12)`
- `App_Start\FilterConfig.cs (line 7, col 8)`
- `App_Start\FilterConfig.cs (line 9, col 12)`
- `App_Start\BundleConfig.cs (line 8, col 8)`
- `App_Start\BundleConfig.cs (line 25, col 12)`
- `App_Start\BundleConfig.cs (line 21, col 12)`
- `App_Start\BundleConfig.cs (line 18, col 12)`
- `App_Start\BundleConfig.cs (line 13, col 12)`
- `App_Start\BundleConfig.cs (line 10, col 12)`

</details>

<details id="NuGet_package_is_incompatible">
<summary><b>NuGet package is incompatible</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="System_Web_Optimization_bundling_and_minification_is_not_supported_in_NET_Core_and_should_be_replaced_with_actual_html_tags_pointing_to_content_files">
<summary><b>System.Web.Optimization bundling and minification is not supported in .NET Core and should be replaced with actual html tags pointing to content files</b> — affected files</summary>

- `Views\Account\Login.cshtml`
- `Views\Account\Manage.cshtml`
- `Views\Account\Register.cshtml`
- `Views\Appointment\Create.cshtml`
- `Views\Appointment\Edit.cshtml`
- `Views\Doctor\Availability.cshtml`
- `Views\Doctor\Create.cshtml`
- `Views\Doctor\Edit.cshtml`
- `Views\RegisteredUsers\Edit.cshtml`
- `Views\Shared\_Layout.cshtml`
- `App_Start\BundleConfig.cs`

</details>

<details id="NuGet_package_functionality_is_included_with_framework_reference">
<summary><b>NuGet package functionality is included with framework reference</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="GlobalFilterCollection_is_not_supported_in_NET_Core_and_needs_to_be_converted_to_the_corresponding_middleware_registrations_on_the_application_object">
<summary><b>GlobalFilterCollection is not supported in .NET Core and needs to be converted to the corresponding middleware registrations on the application object</b> — affected files</summary>

- `Global.asax.cs`
- `App_Start\FilterConfig.cs`

</details>

<details id="Routes_registration_via_RouteCollection_is_not_supported_in_NET_Core_and_needs_to_be_converted_to_the_route_mappings_on_the_application_object">
<summary><b>Routes registration via RouteCollection is not supported in .NET Core and needs to be converted to the route mappings on the application object</b> — affected files</summary>

- `Global.asax.cs`
- `App_Start\RouteConfig.cs`

</details>

<details id="Convert_from_Owin_to_native_ASP_NET_Core_middleware">
<summary><b>Convert from Owin to native ASP.NET Core middleware</b> — affected files</summary>

- `App_Start\Startup.Auth.cs`
- `Startup.cs`

</details>

<details id="Project_file_needs_to_be_converted_to_SDK-style">
<summary><b>Project file needs to be converted to SDK-style</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="Project_s_target_framework_s_needs_to_be_changed">
<summary><b>Project's target framework(s) needs to be changed</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="Default_ASP_NET_identity_should_be_converted_to_AspNetCore_identity">
<summary><b>Default ASP.NET identity should be converted to AspNetCore identity</b> — affected files</summary>

- `Infrastructure\HospitalDbContext.cs`

</details>

<details id="Convert_application_initialization_code_from_Global_asax_cs_to_NET_Core_and_clean_up_Global_asax_cs">
<summary><b>Convert application initialization code from Global.asax.cs to .NET Core and clean up Global.asax.cs</b> — affected files</summary>

- `Global.asax.cs`

</details>

<details id="Source_incompatible_for_selected_NET_version">
<summary><b>Source incompatible for selected .NET version</b> — affected files</summary>

- `Controllers\AccountController.cs (line 186, col 16)`
- `Global.asax.cs (line 65, col 12)`
- `Global.asax.cs (line 62, col 12)`
- `Global.asax.cs (line 58, col 20)`
- `Global.asax.cs (line 42, col 12)`
- `Global.asax.cs (line 37, col 12)`
- `Global.asax.cs (line 35, col 16)`
- `Global.asax.cs (line 28, col 16)`
- `Global.asax.cs (line 27, col 12)`
- `Global.asax.cs (line 22, col 16)`
- `Global.asax.cs (line 21, col 12)`
- `Global.asax.cs (line 9, col 45)`

</details>

<details id="NuGet_package_upgrade_is_recommended">
<summary><b>NuGet package upgrade is recommended</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="Binding_redirect_forces_version_downgrade">
<summary><b>Binding redirect forces version downgrade</b> — affected files</summary>

- `Web.config`

</details>

<details id="NuGet_package_is_deprecated">
<summary><b>NuGet package is deprecated</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

<details id="NuGet_package_contains_security_vulnerability">
<summary><b>NuGet package contains security vulnerability</b> — affected files</summary>

- `DoctorPatient.csproj`

</details>

---

## Codebase Insights

> **Note:** These documents are generated by AI and may contain inaccuracies or incomplete information. Please review carefully.

1. **[Architecture Diagram](facts/architecture-diagram.md)** — Understand the big picture: system layers and component relationships
2. **[Dependency Map](facts/dependency-map.md)** — Know what the project depends on and where the risks are
3. **[API & Service Contracts](facts/api-service-contracts.md)** — See how services communicate and what contracts they expose
4. **[Data Architecture](facts/data-architecture.md)** — Explore data models, storage, and data flow patterns
5. **[Configuration Inventory](facts/configuration-inventory.md)** — Review how the application is configured across environments
6. **[Business Workflows](facts/business-workflows.md)** — Trace end-to-end business processes and domain logic

[Share feedback](https://aka.ms/ghcp-appmod/feedback)
