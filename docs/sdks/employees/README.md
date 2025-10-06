# Employees
(*Employees*)

## Overview

### Available Operations

* [List](#list) - List Employees
* [Create](#create) - Create a new Employee
* [Search](#search) - Search Employees
* [Get](#get) - Get a Employee
* [Delete](#delete) - Delete a Employee
* [Update](#update) - Update a Employee

## List

Returns a paginated list of all `Employees` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeList" method="get" path="/employee" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using Meitner.Models.Requests;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

EmployeeListResponse? res = await sdk.Employees.ListAsync(
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
| `Limit`                                                                                               | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The maximum number of Employees to return (default: 50) when listing Employees                        | 1                                                                                                     |
| `Offset`                                                                                              | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The number of Employees to skip before starting to return results (default: 0) when listing Employees | 0                                                                                                     |

### Response

**[EmployeeListResponse](../../Models/Requests/EmployeeListResponse.md)**

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

Create a new Employee

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeCreate" method="post" path="/employee" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

EmployeeCreate req = new EmployeeCreate() {
    External = new EmployeeCreateExternal() {
        SourceID = "12345678",
    },
    Gender = EmployeeCreateGender.Female,
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    DateOfBirth = DateOnly.Parse("2019-12-16"),
    Address = new EmployeeCreateAddress() {
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
};

var res = await sdk.Employees.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `request`                                                   | [EmployeeCreate](../../Models/Components/EmployeeCreate.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |

### Response

**[EmployeeCreateResponse](../../Models/Requests/EmployeeCreateResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.EmployeeCreate422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |

## Search

Search for `Employees` with filtering capabilities.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeSearch" method="post" path="/employee/_search" -->
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

EmployeeSearchResponse? res = await sdk.Employees.SearchAsync(
    limit: 1,
    offset: 0,
    employeeFilter: new EmployeeFilter() {
        Equals = new EmployeeFilterEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new EmployeeFilterEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new EmployeeFilterEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            IdentityTemporary = true,
            FirstName = "example",
            LastName = "example",
            DateOfBirth = DateOnly.Parse("2024-01-15"),
            Address = new EmployeeFilterEqualsAddress() {
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
        NotEquals = new EmployeeFilterNotEquals() {
            Id = "123e4567-e89b-12d3-a456-426614174000",
            Meta = new EmployeeFilterNotEqualsMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
            },
            External = new EmployeeFilterNotEqualsExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            IdentityTemporary = true,
            FirstName = "example",
            LastName = "example",
            DateOfBirth = DateOnly.Parse("2024-01-15"),
            Address = new EmployeeFilterNotEqualsAddress() {
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
        GreaterThan = new EmployeeFilterGreaterThan() {
            Meta = new EmployeeFilterGreaterThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            DateOfBirth = DateOnly.Parse("2024-01-15"),
        },
        SmallerThan = new EmployeeFilterSmallerThan() {
            Meta = new EmployeeFilterSmallerThanMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            DateOfBirth = DateOnly.Parse("2024-01-15"),
        },
        GreaterOrEqual = new EmployeeFilterGreaterOrEqual() {
            Meta = new EmployeeFilterGreaterOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            DateOfBirth = DateOnly.Parse("2024-01-15"),
        },
        SmallerOrEqual = new EmployeeFilterSmallerOrEqual() {
            Meta = new EmployeeFilterSmallerOrEqualMeta() {
                CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
            },
            DateOfBirth = DateOnly.Parse("2024-01-15"),
        },
        Contains = new EmployeeFilterContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new EmployeeFilterContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new EmployeeFilterContainsExternal() {
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
            DateOfBirth = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            Address = new EmployeeFilterContainsAddress() {
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
        },
        NotContains = new EmployeeFilterNotContains() {
            Id = new List<string>() {
                "123e4567-e89b-12d3-a456-426614174000",
            },
            Meta = new EmployeeFilterNotContainsMeta() {
                CreatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                UpdatedBy = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
            },
            External = new EmployeeFilterNotContainsExternal() {
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
            DateOfBirth = new List<DateOnly>() {
                DateOnly.Parse("2024-01-15"),
            },
            Address = new EmployeeFilterNotContainsAddress() {
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
        },
        Like = new EmployeeFilterLike() {
            External = new EmployeeFilterLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            FirstName = "example",
            LastName = "example",
            Address = new EmployeeFilterLikeAddress() {
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
        NotLike = new EmployeeFilterNotLike() {
            External = new EmployeeFilterNotLikeExternal() {
                SourceID = "example",
                Source = "example",
            },
            IdentityNumber = "example",
            FirstName = "example",
            LastName = "example",
            Address = new EmployeeFilterNotLikeAddress() {
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
        Null = new EmployeeFilterNull() {
            Meta = new EmployeeFilterNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new EmployeeFilterNullExternal() {
                SourceID = true,
                Source = true,
            },
            Gender = true,
            DateOfBirth = true,
            Address = new EmployeeFilterNullAddress() {
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
        },
        NotNull = new EmployeeFilterNotNull() {
            Meta = new EmployeeFilterNotNullMeta() {
                CreatedBy = true,
                UpdatedAt = true,
                UpdatedBy = true,
            },
            External = new EmployeeFilterNotNullExternal() {
                SourceID = true,
                Source = true,
            },
            Gender = true,
            DateOfBirth = true,
            Address = new EmployeeFilterNotNullAddress() {
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
| `Limit`                                                                                                 | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The maximum number of Employees to return (default: 50) when searching Employees                        | 1                                                                                                       |
| `Offset`                                                                                                | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The number of Employees to skip before starting to return results (default: 0) when searching Employees | 0                                                                                                       |
| `EmployeeFilter`                                                                                        | [EmployeeFilter](../../Models/Components/EmployeeFilter.md)                                             | :heavy_minus_sign:                                                                                      | Request body                                                                                            |                                                                                                         |

### Response

**[EmployeeSearchResponse](../../Models/Requests/EmployeeSearchResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.EmployeeSearch422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |

## Get

Retrieves the `Employee` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeGet" method="get" path="/employee/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Employees.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                         | Type                                              | Required                                          | Description                                       | Example                                           |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `Id`                                              | *string*                                          | :heavy_check_mark:                                | The unique identifier of the Employee to retrieve | 123e4567-e89b-12d3-a456-426614174000              |

### Response

**[EmployeeGetResponse](../../Models/Requests/EmployeeGetResponse.md)**

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

Delete a Employee

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeDelete" method="delete" path="/employee/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Employees.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                       | Type                                            | Required                                        | Description                                     | Example                                         |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `Id`                                            | *string*                                        | :heavy_check_mark:                              | The unique identifier of the Employee to delete | 123e4567-e89b-12d3-a456-426614174000            |

### Response

**[EmployeeDeleteResponse](../../Models/Requests/EmployeeDeleteResponse.md)**

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

Update a Employee

### Example Usage

<!-- UsageSnippet language="csharp" operationID="EmployeeUpdate" method="patch" path="/employee/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

var res = await sdk.Employees.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    employeeUpdate: new EmployeeUpdate() {
        External = new EmployeeUpdateExternal() {
            SourceID = "12345678",
        },
        Gender = EmployeeUpdateGender.Female,
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        DateOfBirth = DateOnly.Parse("2019-12-16"),
        Address = new EmployeeUpdateAddress() {
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
    }
);

// handle response
```

### Parameters

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 | Example                                                     |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `Id`                                                        | *string*                                                    | :heavy_check_mark:                                          | The unique identifier of the Employee to update             | 123e4567-e89b-12d3-a456-426614174000                        |
| `EmployeeUpdate`                                            | [EmployeeUpdate](../../Models/Components/EmployeeUpdate.md) | :heavy_check_mark:                                          | Request body                                                |                                                             |

### Response

**[EmployeeUpdateResponse](../../Models/Requests/EmployeeUpdateResponse.md)**

### Errors

| Error Type                                                   | Status Code                                                  | Content Type                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Meitner.Models.Errors.Error400ResponseBody                   | 400                                                          | application/json                                             |
| Meitner.Models.Errors.Error401ResponseBody                   | 401                                                          | application/json                                             |
| Meitner.Models.Errors.Error403ResponseBody                   | 403                                                          | application/json                                             |
| Meitner.Models.Errors.Error404ResponseBody                   | 404                                                          | application/json                                             |
| Meitner.Models.Errors.Error409ResponseBody                   | 409                                                          | application/json                                             |
| Meitner.Models.Errors.EmployeeUpdate422ResponseBodyException | 422                                                          | application/json                                             |
| Meitner.Models.Errors.Error429ResponseBody                   | 429                                                          | application/json                                             |
| Meitner.Models.Errors.Error500ResponseBody                   | 500                                                          | application/json                                             |
| Meitner.Models.Errors.APIException                           | 4XX, 5XX                                                     | \*/\*                                                        |