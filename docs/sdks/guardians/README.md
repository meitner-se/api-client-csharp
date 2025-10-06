# Guardians
(*Guardians*)

## Overview

### Available Operations

* [List](#list) - List Guardians
* [Create](#create) - Create a new Guardian
* [Search](#search) - Search Guardians
* [Get](#get) - Get a Guardian
* [Delete](#delete) - Delete a Guardian
* [Update](#update) - Update a Guardian

## List

Returns a paginated list of all `Guardians` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianList" method="get" path="/guardian" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

GuardianListResponse? res = await sdk.Guardians.ListAsync(
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

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           | Example                                                                                               |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                               | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The maximum number of Guardians to return (default: 50) when listing Guardians                        | 1                                                                                                     |
| `Offset`                                                                                              | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The number of Guardians to skip before starting to return results (default: 0) when listing Guardians | 0                                                                                                     |

### Response

**[GuardianListResponse](../../Models/Requests/GuardianListResponse.md)**

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

Create a new Guardian

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianCreate" method="post" path="/guardian" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

GuardianCreate req = new GuardianCreate() {
    External = new GuardianCreateExternal() {
        SourceID = "12345678",
    },
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    Address = new GuardianCreateAddress() {
        PostalAddress = "Dalvägen 14",
        PostalCode = "169 56",
        PostalCity = "Solna",
        CountryCode = "SWE",
        MunicipalityCode = "0184",
    },
    EmailAddress1 = "lise@meitner.se",
    EmailAddress2 = "lise@gmail.com",
    PhoneNumber1 = "+46701234567",
    PhoneNumber2 = "+46701234567",
    StudentIDs = new List<string>() {
        "123e4567-e89b-12d3-a456-426614174000",
    },
};

var res = await sdk.Guardians.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [GuardianCreate](../../Models/Components/GuardianCreate.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[GuardianCreateResponse](../../Models/Requests/GuardianCreateResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.GuardianCreate422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |

## Search

Search for `Guardians` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianSearch" method="post" path="/guardian/_search" -->
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

GuardianSearchResponse? res = await sdk.Guardians.SearchAsync(
    limit: 1,
    offset: 0,
    guardianFilter: new GuardianFilter() {
        Equals = new GuardianFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new GuardianFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new GuardianFilterEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            IdentityTemporary = true,
            FirstName = "example",
            LastName = "example",
            Address = new GuardianFilterEqualsAddress() {
                PostalAddress = "example",
                PostalCode = "example",
                PostalCity = "example",
                CountryCode = "example",
                MunicipalityCode = "example",
            },
            EmailAddress1 = "example",
            EmailAddress2 = "example",
            PhoneNumber1 = "example",
            PhoneNumber2 = "example",
            StudentIDs = "123e4567-e89b-12d3-a456-426614174000",
        },
        NotEquals = new GuardianFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new GuardianFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new GuardianFilterNotEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            IdentityTemporary = true,
            FirstName = "example",
            LastName = "example",
            Address = new GuardianFilterNotEqualsAddress() {
                PostalAddress = "example",
                PostalCode = "example",
                PostalCity = "example",
                CountryCode = "example",
                MunicipalityCode = "example",
            },
            EmailAddress1 = "example",
            EmailAddress2 = "example",
            PhoneNumber1 = "example",
            PhoneNumber2 = "example",
            StudentIDs = "123e4567-e89b-12d3-a456-426614174000",
        },
        GreaterThan = new GuardianFilterGreaterThan() {
            Meta = new GuardianFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerThan = new GuardianFilterSmallerThan() {
            Meta = new GuardianFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        GreaterOrEqual = new GuardianFilterGreaterOrEqual() {
            Meta = new GuardianFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        SmallerOrEqual = new GuardianFilterSmallerOrEqual() {
            Meta = new GuardianFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
        },
        Contains = new GuardianFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new GuardianFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new GuardianFilterContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            IdentityNumber = new List<string>() {
                "example",
            },
            IdentityTemporary = new List<bool>() {
                true,
            },
            FirstName = new List<string>() {
                "example",
            },
            LastName = new List<string>() {
                "example",
            },
            Address = new GuardianFilterContainsAddress() {
                PostalAddress = new List<string>() {
                    "example",
                },
                PostalCode = new List<string>() {
                    "example",
                },
                PostalCity = new List<string>() {
                    "example",
                },
                CountryCode = new List<string>() {
                    "example",
                },
                MunicipalityCode = new List<string>() {
                    "example",
                },
            },
            EmailAddress1 = new List<string>() {
                "example",
            },
            EmailAddress2 = new List<string>() {
                "example",
            },
            PhoneNumber1 = new List<string>() {
                "example",
            },
            PhoneNumber2 = new List<string>() {
                "example",
            },
            StudentIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        NotContains = new GuardianFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new GuardianFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new GuardianFilterNotContainsExternal() {
                SourceID = new List<string>() {
                    "example",
                },
                Source = new List<string>() {
                    "example",
                },
            },
            IdentityNumber = new List<string>() {
                "example",
            },
            IdentityTemporary = new List<bool>() {
                true,
            },
            FirstName = new List<string>() {
                "example",
            },
            LastName = new List<string>() {
                "example",
            },
            Address = new GuardianFilterNotContainsAddress() {
                PostalAddress = new List<string>() {
                    "example",
                },
                PostalCode = new List<string>() {
                    "example",
                },
                PostalCity = new List<string>() {
                    "example",
                },
                CountryCode = new List<string>() {
                    "example",
                },
                MunicipalityCode = new List<string>() {
                    "example",
                },
            },
            EmailAddress1 = new List<string>() {
                "example",
            },
            EmailAddress2 = new List<string>() {
                "example",
            },
            PhoneNumber1 = new List<string>() {
                "example",
            },
            PhoneNumber2 = new List<string>() {
                "example",
            },
            StudentIDs = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
        },
        Like = new GuardianFilterLike() {
            External = new GuardianFilterLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            FirstName = "example",
            LastName = "example",
            Address = new GuardianFilterLikeAddress() {
                PostalAddress = "example",
                PostalCode = "example",
                PostalCity = "example",
                CountryCode = "example",
                MunicipalityCode = "example",
            },
            EmailAddress1 = "example",
            EmailAddress2 = "example",
            PhoneNumber1 = "example",
            PhoneNumber2 = "example",
        },
        NotLike = new GuardianFilterNotLike() {
            External = new GuardianFilterNotLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            FirstName = "example",
            LastName = "example",
            Address = new GuardianFilterNotLikeAddress() {
                PostalAddress = "example",
                PostalCode = "example",
                PostalCity = "example",
                CountryCode = "example",
                MunicipalityCode = "example",
            },
            EmailAddress1 = "example",
            EmailAddress2 = "example",
            PhoneNumber1 = "example",
            PhoneNumber2 = "example",
        },
        Null = new GuardianFilterNull() {
            Meta = new GuardianFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new GuardianFilterNullExternal() {
                SourceID = true,
                Source = true,
            },
            Address = new GuardianFilterNullAddress() {
                PostalAddress = true,
                PostalCode = true,
                PostalCity = true,
                CountryCode = true,
                MunicipalityCode = true,
            },
            EmailAddress1 = true,
            EmailAddress2 = true,
            PhoneNumber1 = true,
            PhoneNumber2 = true,
            StudentIDs = true,
        },
        NotNull = new GuardianFilterNotNull() {
            Meta = new GuardianFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new GuardianFilterNotNullExternal() {
                SourceID = true,
                Source = true,
            },
            Address = new GuardianFilterNotNullAddress() {
                PostalAddress = true,
                PostalCode = true,
                PostalCity = true,
                CountryCode = true,
                MunicipalityCode = true,
            },
            EmailAddress1 = true,
            EmailAddress2 = true,
            PhoneNumber1 = true,
            PhoneNumber2 = true,
            StudentIDs = true,
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

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                 | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The maximum number of Guardians to return (default: 50) when searching Guardians                        | 1                                                                                                       |
| `Offset`                                                                                                | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The number of Guardians to skip before starting to return results (default: 0) when searching Guardians | 0                                                                                                       |
| `GuardianFilter`                                                                                        | [GuardianFilter](../../Models/Components/GuardianFilter.md)                                             | :heavy_minus_sign:                                                                                      | Request body                                                                                            |                                                                                                         |

### Response

**[GuardianSearchResponse](../../Models/Requests/GuardianSearchResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.GuardianSearch422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |

## Get

Retrieves the `Guardian` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianGet" method="get" path="/guardian/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Guardians.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                         | Type                                              | Required                                          | Description                                       | Example                                           |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `Id`                                              | *string*                                          | :heavy_check_mark:                                | The unique identifier of the Guardian to retrieve | 123e4567-e89b-12d3-a456-426614174000              |

### Response

**[GuardianGetResponse](../../Models/Requests/GuardianGetResponse.md)**

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

Delete a Guardian

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianDelete" method="delete" path="/guardian/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Guardians.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                       | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `Id`                                            | *string*                                        | :heavy_check_mark:                              | The unique identifier of the Guardian to delete | 123e4567-e89b-12d3-a456-426614174000            |

### Response

**[GuardianDeleteResponse](../../Models/Requests/GuardianDeleteResponse.md)**

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

Update a Guardian

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GuardianUpdate" method="patch" path="/guardian/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Guardians.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    guardianUpdate: new GuardianUpdate() {
        External = new GuardianUpdateExternal() {
            SourceID = "12345678",
        },
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        Address = new GuardianUpdateAddress() {
            PostalAddress = "Dalvägen 14",
            PostalCode = "169 56",
            PostalCity = "Solna",
            CountryCode = "SWE",
            MunicipalityCode = "0184",
        },
        EmailAddress1 = "lise@meitner.se",
        EmailAddress2 = "lise@gmail.com",
        PhoneNumber1 = "+46701234567",
        PhoneNumber2 = "+46701234567",
        StudentIDs = new List<string>() {
            "123e4567-e89b-12d3-a456-426614174000",
        },
    }
);

// handle response
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 | Example                                                     |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `Id`                                                        | *string*                                                    | :heavy_check_mark:                                          | The unique identifier of the Guardian to update             | 123e4567-e89b-12d3-a456-426614174000                        |
| `GuardianUpdate`                                            | [GuardianUpdate](../../Models/Components/GuardianUpdate.md) | :heavy_check_mark:                                          | Request body                                                |                                                             |

### Response

**[GuardianUpdateResponse](../../Models/Requests/GuardianUpdateResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.GuardianUpdate422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |