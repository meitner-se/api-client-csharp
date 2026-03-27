# AuditEvents

## Overview

### Available Operations

* [List](#list) - List AuditEvents
* [Search](#search) - Search AuditEvents
* [Get](#get) - Get a AuditEvent

## List

Returns a paginated list of all `AuditEvents` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="AuditEventList" method="get" path="/audit-event" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="AuditEventSearch" method="post" path="/audit-event/_search" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

Models.Requests.AuditEventSearchResponse? res = await sdk.AuditEvents.SearchAsync(
    auditEventSearch: new AuditEventSearchRequestBody() {
        Filter = new AuditEventSearchFilter() {
            Equals = new AuditEventSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new AuditEventSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new AuditEventSearchGreaterThan() {
                Meta = new AuditEventSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new AuditEventSearchSmallerThan() {
                Meta = new AuditEventSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new AuditEventSearchGreaterOrEqual() {
                Meta = new AuditEventSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new AuditEventSearchSmallerOrEqual() {
                Meta = new AuditEventSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new AuditEventSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchContainsMeta() {
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
            NotContains = new AuditEventSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchNotContainsMeta() {
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
            Null = new AuditEventSearchNull() {
                Meta = new AuditEventSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            NotNull = new AuditEventSearchNotNull() {
                Meta = new AuditEventSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            OrCondition = true,
        },
    },
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="AuditEventSearch" method="post" path="/audit-event/_search" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

Models.Requests.AuditEventSearchResponse? res = await sdk.AuditEvents.SearchAsync(
    auditEventSearch: new AuditEventSearchRequestBody() {
        Filter = new AuditEventSearchFilter() {
            Equals = new AuditEventSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new AuditEventSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new AuditEventSearchGreaterThan() {
                Meta = new AuditEventSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new AuditEventSearchSmallerThan() {
                Meta = new AuditEventSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new AuditEventSearchGreaterOrEqual() {
                Meta = new AuditEventSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new AuditEventSearchSmallerOrEqual() {
                Meta = new AuditEventSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new AuditEventSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchContainsMeta() {
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
            NotContains = new AuditEventSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchNotContainsMeta() {
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
            Null = new AuditEventSearchNull() {
                Meta = new AuditEventSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            NotNull = new AuditEventSearchNotNull() {
                Meta = new AuditEventSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            OrCondition = true,
        },
    },
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="AuditEventSearch" method="post" path="/audit-event/_search" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

Models.Requests.AuditEventSearchResponse? res = await sdk.AuditEvents.SearchAsync(
    auditEventSearch: new AuditEventSearchRequestBody() {
        Filter = new AuditEventSearchFilter() {
            Equals = new AuditEventSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new AuditEventSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new AuditEventSearchGreaterThan() {
                Meta = new AuditEventSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new AuditEventSearchSmallerThan() {
                Meta = new AuditEventSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new AuditEventSearchGreaterOrEqual() {
                Meta = new AuditEventSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new AuditEventSearchSmallerOrEqual() {
                Meta = new AuditEventSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new AuditEventSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchContainsMeta() {
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
            NotContains = new AuditEventSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchNotContainsMeta() {
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
            Null = new AuditEventSearchNull() {
                Meta = new AuditEventSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            NotNull = new AuditEventSearchNotNull() {
                Meta = new AuditEventSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            OrCondition = true,
        },
    },
    limit: 1,
    offset: 0
);

while(res != null)
{
    // handle items

    res = await res.Next!();
}
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="AuditEventSearch" method="post" path="/audit-event/_search" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

Models.Requests.AuditEventSearchResponse? res = await sdk.AuditEvents.SearchAsync(
    auditEventSearch: new AuditEventSearchRequestBody() {
        Filter = new AuditEventSearchFilter() {
            Equals = new AuditEventSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new AuditEventSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new AuditEventSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                ResourceID = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new AuditEventSearchGreaterThan() {
                Meta = new AuditEventSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new AuditEventSearchSmallerThan() {
                Meta = new AuditEventSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new AuditEventSearchGreaterOrEqual() {
                Meta = new AuditEventSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new AuditEventSearchSmallerOrEqual() {
                Meta = new AuditEventSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                Timestamp = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new AuditEventSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchContainsMeta() {
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
            NotContains = new AuditEventSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new AuditEventSearchNotContainsMeta() {
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
            Null = new AuditEventSearchNull() {
                Meta = new AuditEventSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            NotNull = new AuditEventSearchNotNull() {
                Meta = new AuditEventSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
            },
            OrCondition = true,
        },
    },
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

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 | Example                                                                                                     |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `AuditEventSearch`                                                                                          | [AuditEventSearchRequestBody](../../Models/Components/AuditEventSearchRequestBody.md)                       | :heavy_check_mark:                                                                                          | Request body                                                                                                |                                                                                                             |
| `Limit`                                                                                                     | *long*                                                                                                      | :heavy_minus_sign:                                                                                          | The maximum number of AuditEvents to return (default: 50) when searching AuditEvents                        | 1                                                                                                           |
| `Offset`                                                                                                    | *long*                                                                                                      | :heavy_minus_sign:                                                                                          | The number of AuditEvents to skip before starting to return results (default: 0) when searching AuditEvents | 0                                                                                                           |

### Response

**[Models.Requests.AuditEventSearchResponse](../../Models/Requests/AuditEventSearchResponse.md)**

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

<!-- UsageSnippet language="csharp" operationID="AuditEventGet" method="get" path="/audit-event/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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