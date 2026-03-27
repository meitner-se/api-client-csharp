# Groups

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

<!-- UsageSnippet language="csharp" operationID="GroupList" method="get" path="/group" example="responseExample" -->
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GroupCreate" method="post" path="/group" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GroupCreate" method="post" path="/group" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GroupCreate" method="post" path="/group" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GroupCreate" method="post" path="/group" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GroupSearch" method="post" path="/group/_search" example="errorExample" -->
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

Models.Requests.GroupSearchResponse? res = await sdk.Groups.SearchAsync(
    groupSearch: new GroupSearchRequestBody() {
        Filter = new GroupSearchFilter() {
            Equals = new GroupSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new GroupSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new GroupSearchGreaterThan() {
                Meta = new GroupSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new GroupSearchSmallerThan() {
                Meta = new GroupSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new GroupSearchGreaterOrEqual() {
                Meta = new GroupSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new GroupSearchSmallerOrEqual() {
                Meta = new GroupSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new GroupSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchContainsExternal() {
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
            NotContains = new GroupSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchNotContainsExternal() {
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
            Like = new GroupSearchLike() {
                External = new GroupSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            NotLike = new GroupSearchNotLike() {
                External = new GroupSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            Null = new GroupSearchNull() {
                Meta = new GroupSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
            },
            NotNull = new GroupSearchNotNull() {
                Meta = new GroupSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
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

<!-- UsageSnippet language="csharp" operationID="GroupSearch" method="post" path="/group/_search" example="requestExample" -->
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

Models.Requests.GroupSearchResponse? res = await sdk.Groups.SearchAsync(
    groupSearch: new GroupSearchRequestBody() {
        Filter = new GroupSearchFilter() {
            Equals = new GroupSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new GroupSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new GroupSearchGreaterThan() {
                Meta = new GroupSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new GroupSearchSmallerThan() {
                Meta = new GroupSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new GroupSearchGreaterOrEqual() {
                Meta = new GroupSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new GroupSearchSmallerOrEqual() {
                Meta = new GroupSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new GroupSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchContainsExternal() {
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
            NotContains = new GroupSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchNotContainsExternal() {
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
            Like = new GroupSearchLike() {
                External = new GroupSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            NotLike = new GroupSearchNotLike() {
                External = new GroupSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            Null = new GroupSearchNull() {
                Meta = new GroupSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
            },
            NotNull = new GroupSearchNotNull() {
                Meta = new GroupSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
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

<!-- UsageSnippet language="csharp" operationID="GroupSearch" method="post" path="/group/_search" example="responseExample" -->
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

Models.Requests.GroupSearchResponse? res = await sdk.Groups.SearchAsync(
    groupSearch: new GroupSearchRequestBody() {
        Filter = new GroupSearchFilter() {
            Equals = new GroupSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new GroupSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new GroupSearchGreaterThan() {
                Meta = new GroupSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new GroupSearchSmallerThan() {
                Meta = new GroupSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new GroupSearchGreaterOrEqual() {
                Meta = new GroupSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new GroupSearchSmallerOrEqual() {
                Meta = new GroupSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new GroupSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchContainsExternal() {
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
            NotContains = new GroupSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchNotContainsExternal() {
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
            Like = new GroupSearchLike() {
                External = new GroupSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            NotLike = new GroupSearchNotLike() {
                External = new GroupSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            Null = new GroupSearchNull() {
                Meta = new GroupSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
            },
            NotNull = new GroupSearchNotNull() {
                Meta = new GroupSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
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

<!-- UsageSnippet language="csharp" operationID="GroupSearch" method="post" path="/group/_search" example="validationError" -->
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

Models.Requests.GroupSearchResponse? res = await sdk.Groups.SearchAsync(
    groupSearch: new GroupSearchRequestBody() {
        Filter = new GroupSearchFilter() {
            Equals = new GroupSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            NotEquals = new GroupSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new GroupSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new GroupSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                Title = "example",
                ModeratorIDs = "123e4567-e89b-12d3-a456-426614174000",
                MemberIDs = "123e4567-e89b-12d3-a456-426614174000",
            },
            GreaterThan = new GroupSearchGreaterThan() {
                Meta = new GroupSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerThan = new GroupSearchSmallerThan() {
                Meta = new GroupSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            GreaterOrEqual = new GroupSearchGreaterOrEqual() {
                Meta = new GroupSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            SmallerOrEqual = new GroupSearchSmallerOrEqual() {
                Meta = new GroupSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
            },
            Contains = new GroupSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchContainsExternal() {
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
            NotContains = new GroupSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new GroupSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new GroupSearchNotContainsExternal() {
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
            Like = new GroupSearchLike() {
                External = new GroupSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            NotLike = new GroupSearchNotLike() {
                External = new GroupSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                Title = "example",
            },
            Null = new GroupSearchNull() {
                Meta = new GroupSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
            },
            NotNull = new GroupSearchNotNull() {
                Meta = new GroupSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new GroupSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Types = true,
                ModeratorIDs = true,
                MemberIDs = true,
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

| Parameter                                                                                         | Type                                                                                              | Required                                                                                          | Description                                                                                       | Example                                                                                           |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `GroupSearch`                                                                                     | [GroupSearchRequestBody](../../Models/Components/GroupSearchRequestBody.md)                       | :heavy_check_mark:                                                                                | Request body                                                                                      |                                                                                                   |
| `Limit`                                                                                           | *long*                                                                                            | :heavy_minus_sign:                                                                                | The maximum number of Groups to return (default: 50) when searching Groups                        | 1                                                                                                 |
| `Offset`                                                                                          | *long*                                                                                            | :heavy_minus_sign:                                                                                | The number of Groups to skip before starting to return results (default: 0) when searching Groups | 0                                                                                                 |

### Response

**[Models.Requests.GroupSearchResponse](../../Models/Requests/GroupSearchResponse.md)**

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

<!-- UsageSnippet language="csharp" operationID="GroupGet" method="get" path="/group/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GroupUpdate" method="patch" path="/group/{id}" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GroupUpdate" method="patch" path="/group/{id}" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GroupUpdate" method="patch" path="/group/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GroupUpdate" method="patch" path="/group/{id}" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
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