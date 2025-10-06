# EmployeePlacements
(*EmployeePlacements*)

## Overview

### Available Operations

* [List](#list) - List EmployeePlacements
* [Create](#create) - Create a new EmployeePlacement
* [Search](#search) - Search EmployeePlacements
* [Get](#get) - Get a EmployeePlacement
* [Delete](#delete) - Delete a EmployeePlacement
* [Update](#update) - Update a EmployeePlacement

## List

Returns a paginated list of all `EmployeePlacements` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementList" method="get" path="/employee-placement" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

EmployeePlacementListResponse? res = await sdk.EmployeePlacements.ListAsync(
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

| Parameter                                                                                                               | Type                                                                                                                    | Required                                                                                                                | Description                                                                                                             | Example                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                                 | *long*                                                                                                                  | :heavy_minus_sign:                                                                                                      | The maximum number of EmployeePlacements to return (default: 50) when listing EmployeePlacements                        | 1                                                                                                                       |
| `Offset`                                                                                                                | *long*                                                                                                                  | :heavy_minus_sign:                                                                                                      | The number of EmployeePlacements to skip before starting to return results (default: 0) when listing EmployeePlacements | 0                                                                                                                       |

### Response

**[EmployeePlacementListResponse](../../Models/Requests/EmployeePlacementListResponse.md)**

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

Create a new EmployeePlacement

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementCreate" method="post" path="/employee-placement" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

EmployeePlacementCreate req = new EmployeePlacementCreate() {
    External = new EmployeePlacementCreateExternal() {
        SourceID = "12345678",
    },
    EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    Signature = "LM",
    Title = "Principal",
    Roles = new List<EmployeePlacementRole>() {
        EmployeePlacementRole.Admin,
    },
    StartDate = DateOnly.Parse("2024-08-01"),
    EndDate = DateOnly.Parse("2024-08-01"),
};

var res = await sdk.EmployeePlacements.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `request`                                                                     | [EmployeePlacementCreate](../../Models/Components/EmployeePlacementCreate.md) | :heavy_check_mark:                                                            | The request object to use for the request.                                    |

### Response

**[EmployeePlacementCreateResponse](../../Models/Requests/EmployeePlacementCreateResponse.md)**

### Errors

| Error Type                                                            | Status Code                                                           | Content Type                                                          |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                            | 400                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error401ResponseBody                            | 401                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error403ResponseBody                            | 403                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error404ResponseBody                            | 404                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error409ResponseBody                            | 409                                                                   | application/json                                                      |
| Meitner.Models.Errors.EmployeePlacementCreate422ResponseBodyException | 422                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error429ResponseBody                            | 429                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error500ResponseBody                            | 500                                                                   | application/json                                                      |
| Meitner.Models.Errors.APIException                                    | 4XX, 5XX                                                              | \*/\*                                                                 |

## Search

Search for `EmployeePlacements` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementSearch" method="post" path="/employee-placement/_search" -->
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

EmployeePlacementSearchResponse? res = await sdk.EmployeePlacements.SearchAsync(
    limit: 1,
    offset: 0,
    employeePlacementFilter: new EmployeePlacementFilter() {
        Equals = new EmployeePlacementFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new EmployeePlacementFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new EmployeePlacementFilterEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
            SchoolID = "123e4567-e89b-12d3-a456-426614174000",
            Signature = "example",
            Title = "example",
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchiveYear = "example",
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        NotEquals = new EmployeePlacementFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new EmployeePlacementFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new EmployeePlacementFilterNotEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
            SchoolID = "123e4567-e89b-12d3-a456-426614174000",
            Signature = "example",
            Title = "example",
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchiveYear = "example",
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        GreaterThan = new EmployeePlacementFilterGreaterThan() {
            Meta = new EmployeePlacementFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        SmallerThan = new EmployeePlacementFilterSmallerThan() {
            Meta = new EmployeePlacementFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        GreaterOrEqual = new EmployeePlacementFilterGreaterOrEqual() {
            Meta = new EmployeePlacementFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        SmallerOrEqual = new EmployeePlacementFilterSmallerOrEqual() {
            Meta = new EmployeePlacementFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            StartDate = DateOnly.Parse("2024-01-15"),
            EndDate = DateOnly.Parse("2024-01-15"),
            ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
        },
        Contains = new EmployeePlacementFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new EmployeePlacementFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new EmployeePlacementFilterContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            EmployeeID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            SchoolID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Signature = new List<string>() {
                "example",
            },
            Title = new List<string>() {
                "example",
            },
            StartDate = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            EndDate = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            ArchiveYear = new List<string>() {
                "example",
            },
        },
        NotContains = new EmployeePlacementFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new EmployeePlacementFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new EmployeePlacementFilterNotContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            EmployeeID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            SchoolID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Signature = new List<string>() {
                "example",
            },
            Title = new List<string>() {
                "example",
            },
            StartDate = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            EndDate = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            ArchiveYear = new List<string>() {
                "example",
            },
        },
        Like = new EmployeePlacementFilterLike() {
            External = new EmployeePlacementFilterLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Signature = "example",
            Title = "example",
            ArchiveYear = "example",
        },
        NotLike = new EmployeePlacementFilterNotLike() {
            External = new EmployeePlacementFilterNotLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Signature = "example",
            Title = "example",
            ArchiveYear = "example",
        },
        Null = new EmployeePlacementFilterNull() {
            Meta = new EmployeePlacementFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new EmployeePlacementFilterNullExternal() {
                SourceID = true,
                Source = true,
            },
            Signature = true,
            Title = true,
            Roles = true,
            EndDate = true,
            ArchiveYear = true,
            ArchivedAt = true,
        },
        NotNull = new EmployeePlacementFilterNotNull() {
            Meta = new EmployeePlacementFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new EmployeePlacementFilterNotNullExternal() {
                SourceID = true,
                Source = true,
            },
            Signature = true,
            Title = true,
            Roles = true,
            EndDate = true,
            ArchiveYear = true,
            ArchivedAt = true,
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

| Parameter                                                                                                                 | Type                                                                                                                      | Required                                                                                                                  | Description                                                                                                               | Example                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                                   | *long*                                                                                                                    | :heavy_minus_sign:                                                                                                        | The maximum number of EmployeePlacements to return (default: 50) when searching EmployeePlacements                        | 1                                                                                                                         |
| `Offset`                                                                                                                  | *long*                                                                                                                    | :heavy_minus_sign:                                                                                                        | The number of EmployeePlacements to skip before starting to return results (default: 0) when searching EmployeePlacements | 0                                                                                                                         |
| `EmployeePlacementFilter`                                                                                                 | [EmployeePlacementFilter](../../Models/Components/EmployeePlacementFilter.md)                                             | :heavy_minus_sign:                                                                                                        | Request body                                                                                                              |                                                                                                                           |

### Response

**[EmployeePlacementSearchResponse](../../Models/Requests/EmployeePlacementSearchResponse.md)**

### Errors

| Error Type                                                            | Status Code                                                           | Content Type                                                          |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                            | 400                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error401ResponseBody                            | 401                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error403ResponseBody                            | 403                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error404ResponseBody                            | 404                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error409ResponseBody                            | 409                                                                   | application/json                                                      |
| Meitner.Models.Errors.EmployeePlacementSearch422ResponseBodyException | 422                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error429ResponseBody                            | 429                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error500ResponseBody                            | 500                                                                   | application/json                                                      |
| Meitner.Models.Errors.APIException                                    | 4XX, 5XX                                                              | \*/\*                                                                 |

## Get

Retrieves the `EmployeePlacement` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementGet" method="get" path="/employee-placement/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.EmployeePlacements.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                  | Type                                                       | Required                                                   | Description                                                | Example                                                    |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `Id`                                                       | *string*                                                   | :heavy_check_mark:                                         | The unique identifier of the EmployeePlacement to retrieve | 123e4567-e89b-12d3-a456-426614174000                       |

### Response

**[EmployeePlacementGetResponse](../../Models/Requests/EmployeePlacementGetResponse.md)**

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

## Delete

Delete a EmployeePlacement

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementDelete" method="delete" path="/employee-placement/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.EmployeePlacements.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `Id`                                                     | *string*                                                 | :heavy_check_mark:                                       | The unique identifier of the EmployeePlacement to delete | 123e4567-e89b-12d3-a456-426614174000                     |

### Response

**[EmployeePlacementDeleteResponse](../../Models/Requests/EmployeePlacementDeleteResponse.md)**

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

Update a EmployeePlacement

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeePlacementUpdate" method="patch" path="/employee-placement/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.EmployeePlacements.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    employeePlacementUpdate: new EmployeePlacementUpdate() {
        External = new EmployeePlacementUpdateExternal() {
            SourceID = "12345678",
        },
        Signature = "LM",
        Title = "Principal",
        Roles = new List<EmployeePlacementRole>() {
            EmployeePlacementRole.Admin,
        },
        StartDate = DateOnly.Parse("2024-08-01"),
        EndDate = DateOnly.Parse("2024-08-01"),
    }
);

// handle response
```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   | Example                                                                       |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `Id`                                                                          | *string*                                                                      | :heavy_check_mark:                                                            | The unique identifier of the EmployeePlacement to update                      | 123e4567-e89b-12d3-a456-426614174000                                          |
| `EmployeePlacementUpdate`                                                     | [EmployeePlacementUpdate](../../Models/Components/EmployeePlacementUpdate.md) | :heavy_check_mark:                                                            | Request body                                                                  |                                                                               |

### Response

**[EmployeePlacementUpdateResponse](../../Models/Requests/EmployeePlacementUpdateResponse.md)**

### Errors

| Error Type                                                            | Status Code                                                           | Content Type                                                          |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                            | 400                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error401ResponseBody                            | 401                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error403ResponseBody                            | 403                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error404ResponseBody                            | 404                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error409ResponseBody                            | 409                                                                   | application/json                                                      |
| Meitner.Models.Errors.EmployeePlacementUpdate422ResponseBodyException | 422                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error429ResponseBody                            | 429                                                                   | application/json                                                      |
| Meitner.Models.Errors.Error500ResponseBody                            | 500                                                                   | application/json                                                      |
| Meitner.Models.Errors.APIException                                    | 4XX, 5XX                                                              | \*/\*                                                                 |