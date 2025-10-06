# Schools
(*Schools*)

## Overview

### Available Operations

* [List](#list) - List Schools
* [Create](#create) - Create a new School
* [Search](#search) - Search Schools
* [Get](#get) - Get a School
* [Update](#update) - Update a School

## List

Returns a paginated list of all `Schools` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="SchoolList" method="get" path="/school" -->
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

### Parameters

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       | Example                                                                                           |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                           | *long*                                                                                            | :heavy_minus_sign:                                                                                | The maximum number of Schools to return (default: 50) when listing Schools                        | 1                                                                                                 |
| `Offset`                                                                                          | *long*                                                                                            | :heavy_minus_sign:                                                                                | The number of Schools to skip before starting to return results (default: 0) when listing Schools | 0                                                                                                 |

### Response

**[SchoolListResponse](../../Models/Requests/SchoolListResponse.md)**

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

Create a new School

### Example Usage

<!-- UsageSnippet language="csharp" operationID="SchoolCreate" method="post" path="/school" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

SchoolCreate req = new SchoolCreate() {
    External = new SchoolCreateExternal() {
        SourceID = "12345678",
    },
    Title = "Meitner Grundskola",
    UnitCode = "12345678",
    CsnSchoolCode = "12345",
    MunicipalityCode = "0184",
    SchoolType = SchoolCreateSchoolType.Grundskola,
};

var res = await sdk.Schools.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `request`                                               | [SchoolCreate](../../Models/Components/SchoolCreate.md) | :heavy_check_mark:                                      | The request object to use for the request.              |

### Response

**[SchoolCreateResponse](../../Models/Requests/SchoolCreateResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                 | 400                                                        | application/json                                           |
| Meitner.Models.Errors.Error401ResponseBody                 | 401                                                        | application/json                                           |
| Meitner.Models.Errors.Error403ResponseBody                 | 403                                                        | application/json                                           |
| Meitner.Models.Errors.Error404ResponseBody                 | 404                                                        | application/json                                           |
| Meitner.Models.Errors.Error409ResponseBody                 | 409                                                        | application/json                                           |
| Meitner.Models.Errors.SchoolCreate422ResponseBodyException | 422                                                        | application/json                                           |
| Meitner.Models.Errors.Error429ResponseBody                 | 429                                                        | application/json                                           |
| Meitner.Models.Errors.Error500ResponseBody                 | 500                                                        | application/json                                           |
| Meitner.Models.Errors.APIException                         | 4XX, 5XX                                                   | \*/\*                                                      |

## Search

Search for `Schools` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="SchoolSearch" method="post" path="/school/_search" -->
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

SchoolSearchResponse? res = await sdk.Schools.SearchAsync(
    limit: 1,
    offset: 0,
    schoolFilter: new SchoolFilter() {
        Equals = new SchoolFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new SchoolFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new SchoolFilterEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
            UnitCode = "example",
            CsnSchoolCode = "example",
            MunicipalityCode = "example",
        },
        NotEquals = new SchoolFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new SchoolFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new SchoolFilterNotEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
            UnitCode = "example",
            CsnSchoolCode = "example",
            MunicipalityCode = "example",
        },
        GreaterThan = new SchoolFilterGreaterThan() {
            Meta = new SchoolFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerThan = new SchoolFilterSmallerThan() {
            Meta = new SchoolFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        GreaterOrEqual = new SchoolFilterGreaterOrEqual() {
            Meta = new SchoolFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerOrEqual = new SchoolFilterSmallerOrEqual() {
            Meta = new SchoolFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        Contains = new SchoolFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new SchoolFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new SchoolFilterContainsExternal() {
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
            UnitCode = new List<string>() {
                "example",
            },
            CsnSchoolCode = new List<string>() {
                "example",
            },
            MunicipalityCode = new List<string>() {
                "example",
            },
        },
        NotContains = new SchoolFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new SchoolFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new SchoolFilterNotContainsExternal() {
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
            UnitCode = new List<string>() {
                "example",
            },
            CsnSchoolCode = new List<string>() {
                "example",
            },
            MunicipalityCode = new List<string>() {
                "example",
            },
        },
        Like = new SchoolFilterLike() {
            External = new SchoolFilterLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
            UnitCode = "example",
            CsnSchoolCode = "example",
            MunicipalityCode = "example",
        },
        NotLike = new SchoolFilterNotLike() {
            External = new SchoolFilterNotLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
            UnitCode = "example",
            CsnSchoolCode = "example",
            MunicipalityCode = "example",
        },
        Null = new SchoolFilterNull() {
            Meta = new SchoolFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new SchoolFilterNullExternal() {
                SourceID = true,
                Source = true,
            },
            UnitCode = true,
            CsnSchoolCode = true,
            MunicipalityCode = true,
        },
        NotNull = new SchoolFilterNotNull() {
            Meta = new SchoolFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new SchoolFilterNotNullExternal() {
                SourceID = true,
                Source = true,
            },
            UnitCode = true,
            CsnSchoolCode = true,
            MunicipalityCode = true,
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

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         | Example                                                                                             |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                             | *long*                                                                                              | :heavy_minus_sign:                                                                                  | The maximum number of Schools to return (default: 50) when searching Schools                        | 1                                                                                                   |
| `Offset`                                                                                            | *long*                                                                                              | :heavy_minus_sign:                                                                                  | The number of Schools to skip before starting to return results (default: 0) when searching Schools | 0                                                                                                   |
| `SchoolFilter`                                                                                      | [SchoolFilter](../../Models/Components/SchoolFilter.md)                                             | :heavy_minus_sign:                                                                                  | Request body                                                                                        |                                                                                                     |

### Response

**[SchoolSearchResponse](../../Models/Requests/SchoolSearchResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                 | 400                                                        | application/json                                           |
| Meitner.Models.Errors.Error401ResponseBody                 | 401                                                        | application/json                                           |
| Meitner.Models.Errors.Error403ResponseBody                 | 403                                                        | application/json                                           |
| Meitner.Models.Errors.Error404ResponseBody                 | 404                                                        | application/json                                           |
| Meitner.Models.Errors.Error409ResponseBody                 | 409                                                        | application/json                                           |
| Meitner.Models.Errors.SchoolSearch422ResponseBodyException | 422                                                        | application/json                                           |
| Meitner.Models.Errors.Error429ResponseBody                 | 429                                                        | application/json                                           |
| Meitner.Models.Errors.Error500ResponseBody                 | 500                                                        | application/json                                           |
| Meitner.Models.Errors.APIException                         | 4XX, 5XX                                                   | \*/\*                                                      |

## Get

Retrieves the `School` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="SchoolGet" method="get" path="/school/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Schools.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                       | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `Id`                                            | *string*                                        | :heavy_check_mark:                              | The unique identifier of the School to retrieve | 123e4567-e89b-12d3-a456-426614174000            |

### Response

**[SchoolGetResponse](../../Models/Requests/SchoolGetResponse.md)**

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

Update a School

### Example Usage

<!-- UsageSnippet language="csharp" operationID="SchoolUpdate" method="patch" path="/school/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Schools.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    schoolUpdate: new SchoolUpdate() {
        External = new SchoolUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "Meitner Grundskola",
        UnitCode = "12345678",
        CsnSchoolCode = "12345",
        MunicipalityCode = "0184",
    }
);

// handle response
```

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             | Example                                                 |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `Id`                                                    | *string*                                                | :heavy_check_mark:                                      | The unique identifier of the School to update           | 123e4567-e89b-12d3-a456-426614174000                    |
| `SchoolUpdate`                                          | [SchoolUpdate](../../Models/Components/SchoolUpdate.md) | :heavy_check_mark:                                      | Request body                                            |                                                         |

### Response

**[SchoolUpdateResponse](../../Models/Requests/SchoolUpdateResponse.md)**

### Errors

| Error Type                                                 | Status Code                                                | Content Type                                               |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                 | 400                                                        | application/json                                           |
| Meitner.Models.Errors.Error401ResponseBody                 | 401                                                        | application/json                                           |
| Meitner.Models.Errors.Error403ResponseBody                 | 403                                                        | application/json                                           |
| Meitner.Models.Errors.Error404ResponseBody                 | 404                                                        | application/json                                           |
| Meitner.Models.Errors.Error409ResponseBody                 | 409                                                        | application/json                                           |
| Meitner.Models.Errors.SchoolUpdate422ResponseBodyException | 422                                                        | application/json                                           |
| Meitner.Models.Errors.Error429ResponseBody                 | 429                                                        | application/json                                           |
| Meitner.Models.Errors.Error500ResponseBody                 | 500                                                        | application/json                                           |
| Meitner.Models.Errors.APIException                         | 4XX, 5XX                                                   | \*/\*                                                      |