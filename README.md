# Meitner

Developer-friendly & type-safe Csharp SDK specifically catered to leverage *Meitner* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=meitner&utm_campaign=csharp"><img src="https://www.speakeasy.com/assets/badges/built-by-speakeasy.svg" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/meitner-2u8/api). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Directory API: Generated API documentation
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [Meitner](#meitner)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Pagination](#pagination)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

### NuGet

To add the [NuGet](https://www.nuget.org/) package to a .NET project:
```bash
dotnet add package Meitner
```

### Locally

To add a reference to a local instance of the SDK in a .NET project:
```bash
dotnet add reference src/Meitner/Meitner.csproj
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security schemes globally:

| Name                | Type   | Scheme  |
| ------------------- | ------ | ------- |
| `ClientCredentials` | apiKey | API key |
| `ClientSecret`      | apiKey | API key |

You can set the security parameters through the `security` optional parameter when initializing the SDK client instance. The selected scheme will be used by default to authenticate with the API for all operations that support it. For example:
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [AuditEvents](docs/sdks/auditevents/README.md)

* [List](docs/sdks/auditevents/README.md#list) - List AuditEvents
* [Search](docs/sdks/auditevents/README.md#search) - Search AuditEvents
* [Get](docs/sdks/auditevents/README.md#get) - Get a AuditEvent

### [EmployeePlacements](docs/sdks/employeeplacements/README.md)

* [List](docs/sdks/employeeplacements/README.md#list) - List EmployeePlacements
* [Create](docs/sdks/employeeplacements/README.md#create) - Create a new EmployeePlacement
* [Search](docs/sdks/employeeplacements/README.md#search) - Search EmployeePlacements
* [Get](docs/sdks/employeeplacements/README.md#get) - Get a EmployeePlacement
* [Delete](docs/sdks/employeeplacements/README.md#delete) - Delete a EmployeePlacement
* [Update](docs/sdks/employeeplacements/README.md#update) - Update a EmployeePlacement

### [Employees](docs/sdks/employees/README.md)

* [List](docs/sdks/employees/README.md#list) - List Employees
* [Create](docs/sdks/employees/README.md#create) - Create a new Employee
* [Search](docs/sdks/employees/README.md#search) - Search Employees
* [Get](docs/sdks/employees/README.md#get) - Get a Employee
* [Delete](docs/sdks/employees/README.md#delete) - Delete a Employee
* [Update](docs/sdks/employees/README.md#update) - Update a Employee

### [Groups](docs/sdks/groups/README.md)

* [List](docs/sdks/groups/README.md#list) - List Groups
* [Create](docs/sdks/groups/README.md#create) - Create a new Group
* [Search](docs/sdks/groups/README.md#search) - Search Groups
* [Get](docs/sdks/groups/README.md#get) - Get a Group
* [Delete](docs/sdks/groups/README.md#delete) - Delete a Group
* [Update](docs/sdks/groups/README.md#update) - Update a Group

### [Guardians](docs/sdks/guardians/README.md)

* [List](docs/sdks/guardians/README.md#list) - List Guardians
* [Create](docs/sdks/guardians/README.md#create) - Create a new Guardian
* [Search](docs/sdks/guardians/README.md#search) - Search Guardians
* [Get](docs/sdks/guardians/README.md#get) - Get a Guardian
* [Delete](docs/sdks/guardians/README.md#delete) - Delete a Guardian
* [Update](docs/sdks/guardians/README.md#update) - Update a Guardian

### [Schools](docs/sdks/schools/README.md)

* [List](docs/sdks/schools/README.md#list) - List Schools
* [Create](docs/sdks/schools/README.md#create) - Create a new School
* [Search](docs/sdks/schools/README.md#search) - Search Schools
* [Get](docs/sdks/schools/README.md#get) - Get a School
* [Update](docs/sdks/schools/README.md#update) - Update a School

### [StudentPlacements](docs/sdks/studentplacements/README.md)

* [List](docs/sdks/studentplacements/README.md#list) - List StudentPlacements
* [Create](docs/sdks/studentplacements/README.md#create) - Create a new StudentPlacement
* [Search](docs/sdks/studentplacements/README.md#search) - Search StudentPlacements
* [Get](docs/sdks/studentplacements/README.md#get) - Get a StudentPlacement
* [Delete](docs/sdks/studentplacements/README.md#delete) - Delete a StudentPlacement
* [Update](docs/sdks/studentplacements/README.md#update) - Update a StudentPlacement
* [Archive](docs/sdks/studentplacements/README.md#archive) - Archive a student placement
* [Restore](docs/sdks/studentplacements/README.md#restore) - Restore an archived student placement

### [Students](docs/sdks/students/README.md)

* [List](docs/sdks/students/README.md#list) - List Students
* [Create](docs/sdks/students/README.md#create) - Create a new Student
* [Search](docs/sdks/students/README.md#search) - Search Students
* [Get](docs/sdks/students/README.md#get) - Get a Student
* [Delete](docs/sdks/students/README.md#delete) - Delete a Student
* [Update](docs/sdks/students/README.md#update) - Update a Student

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Pagination [pagination] -->
## Pagination

Some of the endpoints in this SDK support pagination. To use pagination, you make your SDK calls as usual, but the
returned response object will have a `Next` method that can be called to pull down the next group of results. If the
return value of `Next` is `null`, then there are no more pages to be fetched.

Here's an example of one such pagination call:
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
<!-- End Pagination [pagination] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply pass a `RetryConfig` to the call:
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

SchoolListResponse? res = await sdk.Schools.ListAsync(
    retryConfig: new RetryConfig(
        strategy: RetryConfig.RetryStrategy.BACKOFF,
        backoff: new BackoffStrategy(
            initialIntervalMs: 1L,
            maxIntervalMs: 50L,
            maxElapsedTimeMs: 100L,
            exponent: 1.1
        ),
        retryConnectionErrors: false
    ),
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `RetryConfig` optional parameter when intitializing the SDK:
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(
    retryConfig: new RetryConfig(
        strategy: RetryConfig.RetryStrategy.BACKOFF,
        backoff: new BackoffStrategy(
            initialIntervalMs: 1L,
            maxIntervalMs: 50L,
            maxElapsedTimeMs: 100L,
            exponent: 1.1
        ),
        retryConnectionErrors: false
    ),
    security: new Security() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    }
);

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

[`MeitnerException`](./src/Meitner/Models/Errors/MeitnerException.cs) is the base exception class for all HTTP error responses. It has the following properties:

| Property      | Type                  | Description           |
|---------------|-----------------------|-----------------------|
| `Message`     | *string*              | Error message         |
| `Request`     | *HttpRequestMessage*  | HTTP request object   |
| `Response`    | *HttpResponseMessage* | HTTP response object  |

Some exceptions in this SDK include an additional `Payload` field, which will contain deserialized custom error data when present. Possible exceptions are listed in the [Error Classes](#error-classes) section.

### Example

```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Errors;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

try
{
    SchoolListResponse? res = await sdk.Schools.ListAsync(
        limit: 1,
        offset: 0
    );

    while(res != null)
    {
        // handle items

        res = await res.Next!();
    }
}
catch (MeitnerException ex)  // all SDK exceptions inherit from MeitnerException
{
    // ex.ToString() provides a detailed error message
    System.Console.WriteLine(ex);

    // Base exception fields
    HttpRequestMessage request = ex.Request;
    HttpResponseMessage response = ex.Response;
    var statusCode = (int)response.StatusCode;
    var responseBody = ex.Body;

    if (ex is Error400ResponseBody) // different exceptions may be thrown depending on the method
    {
        // Check error data fields
        Error400ResponseBodyPayload payload = ex.Payload;
        Error400ResponseBodyError Error = payload.Error;
        HTTPMetadata HttpMeta = payload.HttpMeta;
    }

    // An underlying cause may be provided
    if (ex.InnerException != null)
    {
        Exception cause = ex.InnerException;
    }
}
catch (OperationCanceledException ex)
{
    // CancellationToken was cancelled
}
catch (System.Net.Http.HttpRequestException ex)
{
    // Check ex.InnerException for Network connectivity errors
}
```

### Error Classes

**Primary exceptions:**
* [`MeitnerException`](./src/Meitner/Models/Errors/MeitnerException.cs): The base class for HTTP error responses.
  * [`Error400ResponseBody`](./src/Meitner/Models/Errors/Error400ResponseBody.cs): Bad Request - The request was malformed or contained invalid parameters. Status code `400`.
  * [`Error401ResponseBody`](./src/Meitner/Models/Errors/Error401ResponseBody.cs): Unauthorized - The request is missing valid authentication credentials. Status code `401`.
  * [`Error403ResponseBody`](./src/Meitner/Models/Errors/Error403ResponseBody.cs): Forbidden - Request is authenticated, but the user is not allowed to perform the operation. Status code `403`.
  * [`Error404ResponseBody`](./src/Meitner/Models/Errors/Error404ResponseBody.cs): Not Found - The requested resource does not exist. Status code `404`.
  * [`Error409ResponseBody`](./src/Meitner/Models/Errors/Error409ResponseBody.cs): Conflict - The request could not be completed due to a conflict. Status code `409`.
  * [`Error429ResponseBody`](./src/Meitner/Models/Errors/Error429ResponseBody.cs): Too Many Requests - When the rate limit has been exceeded. Status code `429`.
  * [`Error500ResponseBody`](./src/Meitner/Models/Errors/Error500ResponseBody.cs): Internal Server Error - An unexpected server error occurred. Status code `500`.

<details><summary>Less common exceptions (24)</summary>

* [`System.Net.Http.HttpRequestException`](https://learn.microsoft.com/en-us/dotnet/api/system.net.http.httprequestexception): Network connectivity error. For more details about the underlying cause, inspect the `ex.InnerException`.

* Inheriting from [`MeitnerException`](./src/Meitner/Models/Errors/MeitnerException.cs):
  * [`SchoolCreate422ResponseBodyException`](./src/Meitner/Models/Errors/SchoolCreate422ResponseBodyException.cs): Validation error for School Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`SchoolSearch422ResponseBodyException`](./src/Meitner/Models/Errors/SchoolSearch422ResponseBodyException.cs): Validation error for School Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`SchoolUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/SchoolUpdate422ResponseBodyException.cs): Validation error for School Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GroupCreate422ResponseBodyException`](./src/Meitner/Models/Errors/GroupCreate422ResponseBodyException.cs): Validation error for Group Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GroupSearch422ResponseBodyException`](./src/Meitner/Models/Errors/GroupSearch422ResponseBodyException.cs): Validation error for Group Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GroupUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/GroupUpdate422ResponseBodyException.cs): Validation error for Group Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeeCreate422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeeCreate422ResponseBodyException.cs): Validation error for Employee Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeeSearch422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeeSearch422ResponseBodyException.cs): Validation error for Employee Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeeUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeeUpdate422ResponseBodyException.cs): Validation error for Employee Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeePlacementCreate422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeePlacementCreate422ResponseBodyException.cs): Validation error for EmployeePlacement Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeePlacementSearch422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeePlacementSearch422ResponseBodyException.cs): Validation error for EmployeePlacement Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`EmployeePlacementUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/EmployeePlacementUpdate422ResponseBodyException.cs): Validation error for EmployeePlacement Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GuardianCreate422ResponseBodyException`](./src/Meitner/Models/Errors/GuardianCreate422ResponseBodyException.cs): Validation error for Guardian Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GuardianSearch422ResponseBodyException`](./src/Meitner/Models/Errors/GuardianSearch422ResponseBodyException.cs): Validation error for Guardian Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`GuardianUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/GuardianUpdate422ResponseBodyException.cs): Validation error for Guardian Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentCreate422ResponseBodyException`](./src/Meitner/Models/Errors/StudentCreate422ResponseBodyException.cs): Validation error for Student Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentSearch422ResponseBodyException`](./src/Meitner/Models/Errors/StudentSearch422ResponseBodyException.cs): Validation error for Student Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/StudentUpdate422ResponseBodyException.cs): Validation error for Student Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentPlacementCreate422ResponseBodyException`](./src/Meitner/Models/Errors/StudentPlacementCreate422ResponseBodyException.cs): Validation error for StudentPlacement Create operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentPlacementSearch422ResponseBodyException`](./src/Meitner/Models/Errors/StudentPlacementSearch422ResponseBodyException.cs): Validation error for StudentPlacement Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`StudentPlacementUpdate422ResponseBodyException`](./src/Meitner/Models/Errors/StudentPlacementUpdate422ResponseBodyException.cs): Validation error for StudentPlacement Update operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`AuditEventSearch422ResponseBodyException`](./src/Meitner/Models/Errors/AuditEventSearch422ResponseBodyException.cs): Validation error for AuditEvent Search operation - request data failed validation. Status code `422`. Applicable to 1 of 46 methods.*
  * [`ResponseValidationError`](./src/Meitner/Models/Errors/ResponseValidationError.cs): Thrown when the response data could not be deserialized into the expected type.
</details>

\* Refer to the [relevant documentation](#available-resources-and-operations) to determine whether an exception applies to a specific operation.
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Name

You can override the default server globally by passing a server name to the `server: string` optional parameter when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the names associated with the available servers:

| Name         | Server                                        | Description                                     |
| ------------ | --------------------------------------------- | ----------------------------------------------- |
| `production` | `https://api.meitner.se/directory/v1`         | Server to use in production                     |
| `staging`    | `https://api.staging.meitner.se/directory/v1` | Server to use when building and testing the API |

#### Example

```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(
    server: SDKConfig.Server.Production,
    security: new Security() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    }
);

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```

### Override Server URL Per-Client

The default server can also be overridden globally by passing a URL to the `serverUrl: string` optional parameter when initializing the SDK client instance. For example:
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(
    serverUrl: "https://api.meitner.se/directory/v1",
    security: new Security() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    }
);

SchoolListResponse? res = await sdk.Schools.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The C# SDK makes API calls using an `ISpeakeasyHttpClient` that wraps the native
[HttpClient](https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient). This
client provides the ability to attach hooks around the request lifecycle that can be used to modify the request or handle
errors and response.

The `ISpeakeasyHttpClient` interface allows you to either use the default `SpeakeasyHttpClient` that comes with the SDK,
or provide your own custom implementation with customized configuration such as custom message handlers, timeouts,
connection pooling, and other HTTP client settings.

The following example shows how to create a custom HTTP client with request modification and error handling:

```csharp
using Meitner;
using Meitner.Utils;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;

// Create a custom HTTP client
public class CustomHttpClient : ISpeakeasyHttpClient
{
    private readonly ISpeakeasyHttpClient _defaultClient;

    public CustomHttpClient()
    {
        _defaultClient = new SpeakeasyHttpClient();
    }

    public async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken? cancellationToken = null)
    {
        // Add custom header and timeout
        request.Headers.Add("x-custom-header", "custom value");
        request.Headers.Add("x-request-timeout", "30");
        
        try
        {
            var response = await _defaultClient.SendAsync(request, cancellationToken);
            // Log successful response
            Console.WriteLine($"Request successful: {response.StatusCode}");
            return response;
        }
        catch (Exception error)
        {
            // Log error
            Console.WriteLine($"Request failed: {error.Message}");
            throw;
        }
    }

    public void Dispose()
    {
        _httpClient?.Dispose();
        _defaultClient?.Dispose();
    }
}

// Use the custom HTTP client with the SDK
var customHttpClient = new CustomHttpClient();
var sdk = new Meitner(client: customHttpClient);
```

<details>
<summary>You can also provide a completely custom HTTP client with your own configuration:</summary>

```csharp
using Meitner.Utils;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;

// Custom HTTP client with custom configuration
public class AdvancedHttpClient : ISpeakeasyHttpClient
{
    private readonly HttpClient _httpClient;

    public AdvancedHttpClient()
    {
        var handler = new HttpClientHandler()
        {
            MaxConnectionsPerServer = 10,
            // ServerCertificateCustomValidationCallback = customCertValidation, // Custom SSL validation if needed
        };

        _httpClient = new HttpClient(handler)
        {
            Timeout = TimeSpan.FromSeconds(30)
        };
    }

    public async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken? cancellationToken = null)
    {
        return await _httpClient.SendAsync(request, cancellationToken ?? CancellationToken.None);
    }

    public void Dispose()
    {
        _httpClient?.Dispose();
    }
}

var sdk = Meitner.Builder()
    .WithClient(new AdvancedHttpClient())
    .Build();
```
</details>

<details>
<summary>For simple debugging, you can enable request/response logging by implementing a custom client:</summary>

```csharp
public class LoggingHttpClient : ISpeakeasyHttpClient
{
    private readonly ISpeakeasyHttpClient _innerClient;

    public LoggingHttpClient(ISpeakeasyHttpClient innerClient = null)
    {
        _innerClient = innerClient ?? new SpeakeasyHttpClient();
    }

    public async Task<HttpResponseMessage> SendAsync(HttpRequestMessage request, CancellationToken? cancellationToken = null)
    {
        // Log request
        Console.WriteLine($"Sending {request.Method} request to {request.RequestUri}");
        
        var response = await _innerClient.SendAsync(request, cancellationToken);
        
        // Log response
        Console.WriteLine($"Received {response.StatusCode} response");
        
        return response;
    }

    public void Dispose() => _innerClient?.Dispose();
}

var sdk = new Meitner(client: new LoggingHttpClient());
```
</details>

The SDK also provides built-in hook support through the `SDKConfiguration.Hooks` system, which automatically handles
`BeforeRequestAsync`, `AfterSuccessAsync`, and `AfterErrorAsync` hooks for advanced request lifecycle management.
<!-- End Custom HTTP Client [http-client] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=meitner&utm_campaign=csharp)
