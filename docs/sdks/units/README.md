# Units

## Overview

### Available Operations

* [List](#list) - List Units
* [Create](#create) - Create a new Unit
* [Search](#search) - Search Units
* [Get](#get) - Get a Unit
* [Update](#update) - Update a Unit

## List

Returns a paginated list of all `Units` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="UnitList" method="get" path="/unit" example="responseExample" -->
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

UnitListResponse? res = await sdk.Units.ListAsync(
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

| Parameter                                                                                     | Type                                                                                          | Required                                                                                      | Description                                                                                   | Example                                                                                       |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `Limit`                                                                                       | *long*                                                                                        | :heavy_minus_sign:                                                                            | The maximum number of Units to return (default: 50) when listing Units                        | 1                                                                                             |
| `Offset`                                                                                      | *long*                                                                                        | :heavy_minus_sign:                                                                            | The number of Units to skip before starting to return results (default: 0) when listing Units | 0                                                                                             |

### Response

**[UnitListResponse](../../Models/Requests/UnitListResponse.md)**

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

## Create

Create a new Unit

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="UnitCreate" method="post" path="/unit" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

UnitCreate req = new UnitCreate() {
    External = new UnitCreateExternal() {
        SourceID = "12345678",
    },
    Title = "Norra distriktet",
    Description = "Norra grundskole- och förskoleenheten",
};

var res = await sdk.Units.CreateAsync(req);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="UnitCreate" method="post" path="/unit" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

UnitCreate req = new UnitCreate() {
    External = new UnitCreateExternal() {
        SourceID = "12345678",
    },
    Title = "Norra distriktet",
    Description = "Norra grundskole- och förskoleenheten",
};

var res = await sdk.Units.CreateAsync(req);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="UnitCreate" method="post" path="/unit" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

UnitCreate req = new UnitCreate() {
    External = new UnitCreateExternal() {
        SourceID = "12345678",
    },
    Title = "Norra distriktet",
    Description = "Norra grundskole- och förskoleenheten",
};

var res = await sdk.Units.CreateAsync(req);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="UnitCreate" method="post" path="/unit" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

UnitCreate req = new UnitCreate() {
    External = new UnitCreateExternal() {
        SourceID = "12345678",
    },
    Title = "Norra distriktet",
    Description = "Norra grundskole- och förskoleenheten",
};

var res = await sdk.Units.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                           | Type                                                | Required                                            | Description                                         |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `request`                                           | [UnitCreate](../../Models/Components/UnitCreate.md) | :heavy_check_mark:                                  | The request object to use for the request.          |

### Response

**[UnitCreateResponse](../../Models/Requests/UnitCreateResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody               | 400                                                      | application/json                                         |
| Meitner.Models.Errors.Error401ResponseBody               | 401                                                      | application/json                                         |
| Meitner.Models.Errors.Error403ResponseBody               | 403                                                      | application/json                                         |
| Meitner.Models.Errors.Error404ResponseBody               | 404                                                      | application/json                                         |
| Meitner.Models.Errors.Error409ResponseBody               | 409                                                      | application/json                                         |
| Meitner.Models.Errors.UnitCreate422ResponseBodyException | 422                                                      | application/json                                         |
| Meitner.Models.Errors.Error429ResponseBody               | 429                                                      | application/json                                         |
| Meitner.Models.Errors.Error500ResponseBody               | 500                                                      | application/json                                         |
| Meitner.Models.Errors.APIException                       | 4XX, 5XX                                                 | \*/\*                                                    |

## Search

Search for `Units` with filtering capabilities.

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="UnitSearch" method="post" path="/unit/_search" example="errorExample" -->
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

Models.Requests.UnitSearchResponse? res = await sdk.Units.SearchAsync(
    unitSearch: new UnitSearchRequestBody() {
        Filter = new UnitSearchFilter() {
            Equals = new UnitSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotEquals = new UnitSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            GreaterThan = new UnitSearchGreaterThan() {
                Meta = new UnitSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new UnitSearchSmallerThan() {
                Meta = new UnitSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new UnitSearchGreaterOrEqual() {
                Meta = new UnitSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new UnitSearchSmallerOrEqual() {
                Meta = new UnitSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new UnitSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            NotContains = new UnitSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            Like = new UnitSearchLike() {
                External = new UnitSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotLike = new UnitSearchNotLike() {
                External = new UnitSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            Null = new UnitSearchNull() {
                Meta = new UnitSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
            },
            NotNull = new UnitSearchNotNull() {
                Meta = new UnitSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
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

<!-- UsageSnippet language="csharp" operationID="UnitSearch" method="post" path="/unit/_search" example="requestExample" -->
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

Models.Requests.UnitSearchResponse? res = await sdk.Units.SearchAsync(
    unitSearch: new UnitSearchRequestBody() {
        Filter = new UnitSearchFilter() {
            Equals = new UnitSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotEquals = new UnitSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            GreaterThan = new UnitSearchGreaterThan() {
                Meta = new UnitSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new UnitSearchSmallerThan() {
                Meta = new UnitSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new UnitSearchGreaterOrEqual() {
                Meta = new UnitSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new UnitSearchSmallerOrEqual() {
                Meta = new UnitSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new UnitSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            NotContains = new UnitSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            Like = new UnitSearchLike() {
                External = new UnitSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotLike = new UnitSearchNotLike() {
                External = new UnitSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            Null = new UnitSearchNull() {
                Meta = new UnitSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
            },
            NotNull = new UnitSearchNotNull() {
                Meta = new UnitSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
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

<!-- UsageSnippet language="csharp" operationID="UnitSearch" method="post" path="/unit/_search" example="responseExample" -->
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

Models.Requests.UnitSearchResponse? res = await sdk.Units.SearchAsync(
    unitSearch: new UnitSearchRequestBody() {
        Filter = new UnitSearchFilter() {
            Equals = new UnitSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotEquals = new UnitSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            GreaterThan = new UnitSearchGreaterThan() {
                Meta = new UnitSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new UnitSearchSmallerThan() {
                Meta = new UnitSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new UnitSearchGreaterOrEqual() {
                Meta = new UnitSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new UnitSearchSmallerOrEqual() {
                Meta = new UnitSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new UnitSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            NotContains = new UnitSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            Like = new UnitSearchLike() {
                External = new UnitSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotLike = new UnitSearchNotLike() {
                External = new UnitSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            Null = new UnitSearchNull() {
                Meta = new UnitSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
            },
            NotNull = new UnitSearchNotNull() {
                Meta = new UnitSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
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

<!-- UsageSnippet language="csharp" operationID="UnitSearch" method="post" path="/unit/_search" example="validationError" -->
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

Models.Requests.UnitSearchResponse? res = await sdk.Units.SearchAsync(
    unitSearch: new UnitSearchRequestBody() {
        Filter = new UnitSearchFilter() {
            Equals = new UnitSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotEquals = new UnitSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new UnitSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new UnitSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            GreaterThan = new UnitSearchGreaterThan() {
                Meta = new UnitSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new UnitSearchSmallerThan() {
                Meta = new UnitSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new UnitSearchGreaterOrEqual() {
                Meta = new UnitSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new UnitSearchSmallerOrEqual() {
                Meta = new UnitSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new UnitSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            NotContains = new UnitSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new UnitSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new UnitSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                Title = new List<string>() {
                    "example",
                },
                Description = new List<string>() {
                    "example",
                },
            },
            Like = new UnitSearchLike() {
                External = new UnitSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            NotLike = new UnitSearchNotLike() {
                External = new UnitSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
                Description = "example",
            },
            Null = new UnitSearchNull() {
                Meta = new UnitSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
            },
            NotNull = new UnitSearchNotNull() {
                Meta = new UnitSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new UnitSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Description = true,
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

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `UnitSearch`                                                                                    | [UnitSearchRequestBody](../../Models/Components/UnitSearchRequestBody.md)                       | :heavy_check_mark:                                                                              | Request body                                                                                    |                                                                                                 |
| `Limit`                                                                                         | *long*                                                                                          | :heavy_minus_sign:                                                                              | The maximum number of Units to return (default: 50) when searching Units                        | 1                                                                                               |
| `Offset`                                                                                        | *long*                                                                                          | :heavy_minus_sign:                                                                              | The number of Units to skip before starting to return results (default: 0) when searching Units | 0                                                                                               |

### Response

**[Models.Requests.UnitSearchResponse](../../Models/Requests/UnitSearchResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody               | 400                                                      | application/json                                         |
| Meitner.Models.Errors.Error401ResponseBody               | 401                                                      | application/json                                         |
| Meitner.Models.Errors.Error403ResponseBody               | 403                                                      | application/json                                         |
| Meitner.Models.Errors.Error404ResponseBody               | 404                                                      | application/json                                         |
| Meitner.Models.Errors.Error409ResponseBody               | 409                                                      | application/json                                         |
| Meitner.Models.Errors.UnitSearch422ResponseBodyException | 422                                                      | application/json                                         |
| Meitner.Models.Errors.Error429ResponseBody               | 429                                                      | application/json                                         |
| Meitner.Models.Errors.Error500ResponseBody               | 500                                                      | application/json                                         |
| Meitner.Models.Errors.APIException                       | 4XX, 5XX                                                 | \*/\*                                                    |

## Get

Retrieves the `Unit` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="UnitGet" method="get" path="/unit/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Units.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                     | Type                                          | Required                                      | Description                                   | Example                                       |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| `Id`                                          | *string*                                      | :heavy_check_mark:                            | The unique identifier of the Unit to retrieve | 123e4567-e89b-12d3-a456-426614174000          |

### Response

**[UnitGetResponse](../../Models/Requests/UnitGetResponse.md)**

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

## Update

Update a Unit

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Units.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    unitUpdate: new UnitUpdate() {
        External = new UnitUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "Norra distriktet",
        Description = "Norra grundskole- och förskoleenheten",
    }
);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Units.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    unitUpdate: new UnitUpdate() {
        External = new UnitUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "Norra distriktet",
        Description = "Norra grundskole- och förskoleenheten",
    }
);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Units.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    unitUpdate: new UnitUpdate() {
        External = new UnitUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "Norra distriktet",
        Description = "Norra grundskole- och förskoleenheten",
    }
);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="UnitUpdate" method="patch" path="/unit/{id}" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Units.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    unitUpdate: new UnitUpdate() {
        External = new UnitUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "Norra distriktet",
        Description = "Norra grundskole- och förskoleenheten",
    }
);

// handle response
```

### Parameters

| Parameter                                           | Type                                                | Required                                            | Description                                         | Example                                             |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `Id`                                                | *string*                                            | :heavy_check_mark:                                  | The unique identifier of the Unit to update         | 123e4567-e89b-12d3-a456-426614174000                |
| `UnitUpdate`                                        | [UnitUpdate](../../Models/Components/UnitUpdate.md) | :heavy_check_mark:                                  | Request body                                        |                                                     |

### Response

**[UnitUpdateResponse](../../Models/Requests/UnitUpdateResponse.md)**

### Errors

| Error Type                                               | Status Code                                              | Content Type                                             |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody               | 400                                                      | application/json                                         |
| Meitner.Models.Errors.Error401ResponseBody               | 401                                                      | application/json                                         |
| Meitner.Models.Errors.Error403ResponseBody               | 403                                                      | application/json                                         |
| Meitner.Models.Errors.Error404ResponseBody               | 404                                                      | application/json                                         |
| Meitner.Models.Errors.Error409ResponseBody               | 409                                                      | application/json                                         |
| Meitner.Models.Errors.UnitUpdate422ResponseBodyException | 422                                                      | application/json                                         |
| Meitner.Models.Errors.Error429ResponseBody               | 429                                                      | application/json                                         |
| Meitner.Models.Errors.Error500ResponseBody               | 500                                                      | application/json                                         |
| Meitner.Models.Errors.APIException                       | 4XX, 5XX                                                 | \*/\*                                                    |