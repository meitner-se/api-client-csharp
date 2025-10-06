# Groups
(*Groups*)

## Overview

### Available Operations

* [List](#list) - List Groups
* [Create](#create) - Create a new Group
* [Search](#search) - Search Groups
* [Get](#get) - Get a Group
* [Delete](#delete) - Delete a Group
* [Update](#update) - Update a Group

## List

Returns a paginated list of all `Groups` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupList" method="get" path="/group" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

GroupListResponse? res = await sdk.Groups.ListAsync(
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
| `Limit`                                                                                         | *long*                                                                                          | :heavy_minus_sign:                                                                              | The maximum number of Groups to return (default: 50) when listing Groups                        | 1                                                                                               |
| `Offset`                                                                                        | *long*                                                                                          | :heavy_minus_sign:                                                                              | The number of Groups to skip before starting to return results (default: 0) when listing Groups | 0                                                                                               |

### Response

**[GroupListResponse](../../Models/Requests/GroupListResponse.md)**

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

Create a new Group

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupCreate" method="post" path="/group" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

GroupCreate req = new GroupCreate() {
    External = new GroupCreateExternal() {
        SourceID = "12345678",
    },
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    Title = "1A",
    Types = new List<GroupType>() {
        GroupType.Class,
    },
    ModeratorIDs = new List<string>() {
        "123e4567-e89b-12d3-a456-426614174000",
    },
    MemberIDs = new List<string>() {
        "123e4567-e89b-12d3-a456-426614174000",
    },
};

var res = await sdk.Groups.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `request`                                             | [GroupCreate](../../Models/Components/GroupCreate.md) | :heavy_check_mark:                                    | The request object to use for the request.            |

### Response

**[GroupCreateResponse](../../Models/Requests/GroupCreateResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                | 400                                                       | application/json                                          |
| Meitner.Models.Errors.Error401ResponseBody                | 401                                                       | application/json                                          |
| Meitner.Models.Errors.Error403ResponseBody                | 403                                                       | application/json                                          |
| Meitner.Models.Errors.Error404ResponseBody                | 404                                                       | application/json                                          |
| Meitner.Models.Errors.Error409ResponseBody                | 409                                                       | application/json                                          |
| Meitner.Models.Errors.GroupCreate422ResponseBodyException | 422                                                       | application/json                                          |
| Meitner.Models.Errors.Error429ResponseBody                | 429                                                       | application/json                                          |
| Meitner.Models.Errors.Error500ResponseBody                | 500                                                       | application/json                                          |
| Meitner.Models.Errors.APIException                        | 4XX, 5XX                                                  | \*/\*                                                     |

## Search

Search for `Groups` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupSearch" method="post" path="/group/_search" -->
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

GroupSearchResponse? res = await sdk.Groups.SearchAsync(
    limit: 1,
    offset: 0,
    groupFilter: new GroupFilter() {
        Equals = new GroupFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new GroupFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new GroupFilterEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            SchoolID = "123e4567-e89b-12d3-a456-426614174000",
            Title = "example",
            ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
            MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
        },
        NotEquals = new GroupFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new GroupFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new GroupFilterNotEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            SchoolID = "123e4567-e89b-12d3-a456-426614174000",
            Title = "example",
            ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
            MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
        },
        GreaterThan = new GroupFilterGreaterThan() {
            Meta = new GroupFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerThan = new GroupFilterSmallerThan() {
            Meta = new GroupFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        GreaterOrEqual = new GroupFilterGreaterOrEqual() {
            Meta = new GroupFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerOrEqual = new GroupFilterSmallerOrEqual() {
            Meta = new GroupFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        Contains = new GroupFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new GroupFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new GroupFilterContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            SchoolID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Title = new List<string>() {
                "example",
            },
            ModeratorIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            MemberIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        NotContains = new GroupFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new GroupFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new GroupFilterNotContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            SchoolID = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Title = new List<string>() {
                "example",
            },
            ModeratorIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            MemberIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        Like = new GroupFilterLike() {
            External = new GroupFilterLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
        },
        NotLike = new GroupFilterNotLike() {
            External = new GroupFilterNotLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            Title = "example",
        },
        Null = new GroupFilterNull() {
            Meta = new GroupFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new GroupFilterNullExternal() {
                SourceID = true,
                Source = true,
            },
            Types = true,
            ModeratorIDs = true,
            MemberIDs = true,
        },
        NotNull = new GroupFilterNotNull() {
            Meta = new GroupFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new GroupFilterNotNullExternal() {
                SourceID = true,
                Source = true,
            },
            Types = true,
            ModeratorIDs = true,
            MemberIDs = true,
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

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       | Example                                                                                           |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                           | *long*                                                                                            | :heavy_minus_sign:                                                                                | The maximum number of Groups to return (default: 50) when searching Groups                        | 1                                                                                                 |
| `Offset`                                                                                          | *long*                                                                                            | :heavy_minus_sign:                                                                                | The number of Groups to skip before starting to return results (default: 0) when searching Groups | 0                                                                                                 |
| `GroupFilter`                                                                                     | [GroupFilter](../../Models/Components/GroupFilter.md)                                             | :heavy_minus_sign:                                                                                | Request body                                                                                      |                                                                                                   |

### Response

**[GroupSearchResponse](../../Models/Requests/GroupSearchResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                | 400                                                       | application/json                                          |
| Meitner.Models.Errors.Error401ResponseBody                | 401                                                       | application/json                                          |
| Meitner.Models.Errors.Error403ResponseBody                | 403                                                       | application/json                                          |
| Meitner.Models.Errors.Error404ResponseBody                | 404                                                       | application/json                                          |
| Meitner.Models.Errors.Error409ResponseBody                | 409                                                       | application/json                                          |
| Meitner.Models.Errors.GroupSearch422ResponseBodyException | 422                                                       | application/json                                          |
| Meitner.Models.Errors.Error429ResponseBody                | 429                                                       | application/json                                          |
| Meitner.Models.Errors.Error500ResponseBody                | 500                                                       | application/json                                          |
| Meitner.Models.Errors.APIException                        | 4XX, 5XX                                                  | \*/\*                                                     |

## Get

Retrieves the `Group` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupGet" method="get" path="/group/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Groups.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                      | Type                                           | Required                                       | Description                                    | Example                                        |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `Id`                                           | *string*                                       | :heavy_check_mark:                             | The unique identifier of the Group to retrieve | 123e4567-e89b-12d3-a456-426614174000           |

### Response

**[GroupGetResponse](../../Models/Requests/GroupGetResponse.md)**

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

Delete a Group

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupDelete" method="delete" path="/group/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Groups.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                    | Type                                         | Required                                     | Description                                  | Example                                      |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| `Id`                                         | *string*                                     | :heavy_check_mark:                           | The unique identifier of the Group to delete | 123e4567-e89b-12d3-a456-426614174000         |

### Response

**[GroupDeleteResponse](../../Models/Requests/GroupDeleteResponse.md)**

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

Update a Group

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GroupUpdate" method="patch" path="/group/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Groups.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    groupUpdate: new GroupUpdate() {
        External = new GroupUpdateExternal() {
            SourceID = "12345678",
        },
        Title = "1A",
        Types = new List<GroupType>() {
            GroupType.Class,
        },
        ModeratorIDs = new List<string>() {
            "123e4567-e89b-12d3-a456-426614174000",
        },
        MemberIDs = new List<string>() {
            "123e4567-e89b-12d3-a456-426614174000",
        },
    }
);

// handle response
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           | Example                                               |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `Id`                                                  | *string*                                              | :heavy_check_mark:                                    | The unique identifier of the Group to update          | 123e4567-e89b-12d3-a456-426614174000                  |
| `GroupUpdate`                                         | [GroupUpdate](../../Models/Components/GroupUpdate.md) | :heavy_check_mark:                                    | Request body                                          |                                                       |

### Response

**[GroupUpdateResponse](../../Models/Requests/GroupUpdateResponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                | 400                                                       | application/json                                          |
| Meitner.Models.Errors.Error401ResponseBody                | 401                                                       | application/json                                          |
| Meitner.Models.Errors.Error403ResponseBody                | 403                                                       | application/json                                          |
| Meitner.Models.Errors.Error404ResponseBody                | 404                                                       | application/json                                          |
| Meitner.Models.Errors.Error409ResponseBody                | 409                                                       | application/json                                          |
| Meitner.Models.Errors.GroupUpdate422ResponseBodyException | 422                                                       | application/json                                          |
| Meitner.Models.Errors.Error429ResponseBody                | 429                                                       | application/json                                          |
| Meitner.Models.Errors.Error500ResponseBody                | 500                                                       | application/json                                          |
| Meitner.Models.Errors.APIException                        | 4XX, 5XX                                                  | \*/\*                                                     |