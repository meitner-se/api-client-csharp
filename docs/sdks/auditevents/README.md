# AuditEvents
(*AuditEvents*)

## Overview

### Available Operations

* [List](#list) - List AuditEvents
* [Search](#search) - Search AuditEvents
* [Get](#get) - Get a AuditEvent

## List

Returns a paginated list of all `AuditEvents` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="AuditEventList" method="get" path="/audit-event" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

AuditEventListResponse? res = await sdk.AuditEvents.ListAsync(
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               | Example                                                                                                   |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                   | *long*                                                                                                    | :heavy_minus_sign:                                                                                        | The maximum number of AuditEvents to return (default: 50) when listing AuditEvents                        | 1                                                                                                         |
| `Offset`                                                                                                  | *long*                                                                                                    | :heavy_minus_sign:                                                                                        | The number of AuditEvents to skip before starting to return results (default: 0) when listing AuditEvents | 0                                                                                                         |

### Response

**[AuditEventListResponse](../../Models/Requests/AuditEventListResponse.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody | 400                                        | application/json                           |
| Meitner.Models.Errors.Error401ResponseBody | 401                                        | application/json                           |
| Meitner.Models.Errors.Error403ResponseBody | 403                                        | application/json                           |
| Meitner.Models.Errors.Error404ResponseBody | 404                                        | application/json                           |
| Meitner.Models.Errors.Error409ResponseBody | 409                                        | application/json                           |
| Meitner.Models.Errors.Error429ResponseBody | 429                                        | application/json                           |
| Meitner.Models.Errors.Error500ResponseBody | 500                                        | application/json                           |
| Meitner.Models.Errors.APIException         | 4XX, 5XX                                   | \*/\*                                      |

## Search

Search for `AuditEvents` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="AuditEventSearch" method="post" path="/audit-event/_search" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

AuditEventSearchResponse? res = await sdk.AuditEvents.SearchAsync(
    limit: 1,
    offset: 0,
    auditEventFilter: new AuditEventFilter() {
        Equals = new AuditEventFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new AuditEventFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            ResourceID = "123e4567-e89b-12d3-a456-426614174000",
        },
        NotEquals = new AuditEventFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new AuditEventFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            ResourceID = "123e4567-e89b-12d3-a456-426614174000",
        },
        GreaterThan = new AuditEventFilterGreaterThan() {
            Meta = new AuditEventFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        SmallerThan = new AuditEventFilterSmallerThan() {
            Meta = new AuditEventFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        GreaterOrEqual = new AuditEventFilterGreaterOrEqual() {
            Meta = new AuditEventFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        SmallerOrEqual = new AuditEventFilterSmallerOrEqual() {
            Meta = new AuditEventFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        Contains = new AuditEventFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new AuditEventFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            ResourceID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        NotContains = new AuditEventFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new AuditEventFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            ResourceID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        Null = new AuditEventFilterNull() {
            Meta = new AuditEventFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
        },
        NotNull = new AuditEventFilterNotNull() {
            Meta = new AuditEventFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
        },
        OrCondition = true,
    }
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 | Example                                                                                                     |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                     | *long*                                                                                                      | :heavy_minus_sign:                                                                                          | The maximum number of AuditEvents to return (default: 50) when searching AuditEvents                        | 1                                                                                                           |
| `Offset`                                                                                                    | *long*                                                                                                      | :heavy_minus_sign:                                                                                          | The number of AuditEvents to skip before starting to return results (default: 0) when searching AuditEvents | 0                                                                                                           |
| `AuditEventFilter`                                                                                          | [AuditEventFilter](../../Models/Components/AuditEventFilter.md)                                             | :heavy_minus_sign:                                                                                          | Request body                                                                                                |                                                                                                             |

### Response

**[AuditEventSearchResponse](../../Models/Requests/AuditEventSearchResponse.md)**

### Errors

| Error Type                                                     | Status Code                                                    | Content Type                                                   |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                     | 400                                                            | application/json                                               |
| Meitner.Models.Errors.Error401ResponseBody                     | 401                                                            | application/json                                               |
| Meitner.Models.Errors.Error403ResponseBody                     | 403                                                            | application/json                                               |
| Meitner.Models.Errors.Error404ResponseBody                     | 404                                                            | application/json                                               |
| Meitner.Models.Errors.Error409ResponseBody                     | 409                                                            | application/json                                               |
| Meitner.Models.Errors.AuditEventSearch422ResponseBodyException | 422                                                            | application/json                                               |
| Meitner.Models.Errors.Error429ResponseBody                     | 429                                                            | application/json                                               |
| Meitner.Models.Errors.Error500ResponseBody                     | 500                                                            | application/json                                               |
| Meitner.Models.Errors.APIException                             | 4XX, 5XX                                                       | \*/\*                                                          |

## Get

Retrieves the `AuditEvent` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="AuditEventGet" method="get" path="/audit-event/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.AuditEvents.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                           | Type                                                | Required                                            | Description                                         | Example                                             |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `Id`                                                | *string*                                            | :heavy_check_mark:                                  | The unique identifier of the AuditEvent to retrieve | 123e4567-e89b-12d3-a456-426614174000                |

### Response

**[AuditEventGetResponse](../../Models/Requests/AuditEventGetResponse.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody | 400                                        | application/json                           |
| Meitner.Models.Errors.Error401ResponseBody | 401                                        | application/json                           |
| Meitner.Models.Errors.Error403ResponseBody | 403                                        | application/json                           |
| Meitner.Models.Errors.Error404ResponseBody | 404                                        | application/json                           |
| Meitner.Models.Errors.Error409ResponseBody | 409                                        | application/json                           |
| Meitner.Models.Errors.Error429ResponseBody | 429                                        | application/json                           |
| Meitner.Models.Errors.Error500ResponseBody | 500                                        | application/json                           |
| Meitner.Models.Errors.APIException         | 4XX, 5XX                                   | \*/\*                                      |