# Employees

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

<!-- UsageSnippet language="csharp" operationID="EmployeeList" method="get" path="/employee" example="responseExample" -->
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="EmployeeCreate" method="post" path="/employee" example="errorExample" -->
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
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="EmployeeCreate" method="post" path="/employee" example="requestExample" -->
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
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="EmployeeCreate" method="post" path="/employee" example="responseExample" -->
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
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="EmployeeCreate" method="post" path="/employee" example="validationError" -->
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="EmployeeSearch" method="post" path="/employee/_search" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

Models.Requests.EmployeeSearchResponse? res = await sdk.Employees.SearchAsync(
    employeeSearch: new EmployeeSearchRequestBody() {
        Filter = new EmployeeSearchFilter() {
            Equals = new EmployeeSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchEqualsAddress() {
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
            NotEquals = new EmployeeSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchNotEqualsAddress() {
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
            GreaterThan = new EmployeeSearchGreaterThan() {
                Meta = new EmployeeSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new EmployeeSearchSmallerThan() {
                Meta = new EmployeeSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new EmployeeSearchGreaterOrEqual() {
                Meta = new EmployeeSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new EmployeeSearchSmallerOrEqual() {
                Meta = new EmployeeSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new EmployeeSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchContainsExternal() {
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
                Address = new EmployeeSearchContainsAddress() {
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
            NotContains = new EmployeeSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchNotContainsExternal() {
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
                Address = new EmployeeSearchNotContainsAddress() {
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
            Like = new EmployeeSearchLike() {
                External = new EmployeeSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchLikeAddress() {
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
            NotLike = new EmployeeSearchNotLike() {
                External = new EmployeeSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchNotLikeAddress() {
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
            Null = new EmployeeSearchNull() {
                Meta = new EmployeeSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNullAddress() {
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
            NotNull = new EmployeeSearchNotNull() {
                Meta = new EmployeeSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNotNullAddress() {
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

<!-- UsageSnippet language="csharp" operationID="EmployeeSearch" method="post" path="/employee/_search" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

Models.Requests.EmployeeSearchResponse? res = await sdk.Employees.SearchAsync(
    employeeSearch: new EmployeeSearchRequestBody() {
        Filter = new EmployeeSearchFilter() {
            Equals = new EmployeeSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchEqualsAddress() {
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
            NotEquals = new EmployeeSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchNotEqualsAddress() {
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
            GreaterThan = new EmployeeSearchGreaterThan() {
                Meta = new EmployeeSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new EmployeeSearchSmallerThan() {
                Meta = new EmployeeSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new EmployeeSearchGreaterOrEqual() {
                Meta = new EmployeeSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new EmployeeSearchSmallerOrEqual() {
                Meta = new EmployeeSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new EmployeeSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchContainsExternal() {
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
                Address = new EmployeeSearchContainsAddress() {
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
            NotContains = new EmployeeSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchNotContainsExternal() {
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
                Address = new EmployeeSearchNotContainsAddress() {
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
            Like = new EmployeeSearchLike() {
                External = new EmployeeSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchLikeAddress() {
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
            NotLike = new EmployeeSearchNotLike() {
                External = new EmployeeSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchNotLikeAddress() {
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
            Null = new EmployeeSearchNull() {
                Meta = new EmployeeSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNullAddress() {
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
            NotNull = new EmployeeSearchNotNull() {
                Meta = new EmployeeSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNotNullAddress() {
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

<!-- UsageSnippet language="csharp" operationID="EmployeeSearch" method="post" path="/employee/_search" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

Models.Requests.EmployeeSearchResponse? res = await sdk.Employees.SearchAsync(
    employeeSearch: new EmployeeSearchRequestBody() {
        Filter = new EmployeeSearchFilter() {
            Equals = new EmployeeSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchEqualsAddress() {
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
            NotEquals = new EmployeeSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchNotEqualsAddress() {
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
            GreaterThan = new EmployeeSearchGreaterThan() {
                Meta = new EmployeeSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new EmployeeSearchSmallerThan() {
                Meta = new EmployeeSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new EmployeeSearchGreaterOrEqual() {
                Meta = new EmployeeSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new EmployeeSearchSmallerOrEqual() {
                Meta = new EmployeeSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new EmployeeSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchContainsExternal() {
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
                Address = new EmployeeSearchContainsAddress() {
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
            NotContains = new EmployeeSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchNotContainsExternal() {
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
                Address = new EmployeeSearchNotContainsAddress() {
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
            Like = new EmployeeSearchLike() {
                External = new EmployeeSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchLikeAddress() {
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
            NotLike = new EmployeeSearchNotLike() {
                External = new EmployeeSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchNotLikeAddress() {
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
            Null = new EmployeeSearchNull() {
                Meta = new EmployeeSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNullAddress() {
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
            NotNull = new EmployeeSearchNotNull() {
                Meta = new EmployeeSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNotNullAddress() {
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

<!-- UsageSnippet language="csharp" operationID="EmployeeSearch" method="post" path="/employee/_search" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;
using System.Collections.Generic;

var sdk = new MeitnerSDK(security: new Security() {
    ClientCredentials = "<YOUR_API_KEY_HERE>",
    ClientSecret = "<YOUR_API_KEY_HERE>",
});

Models.Requests.EmployeeSearchResponse? res = await sdk.Employees.SearchAsync(
    employeeSearch: new EmployeeSearchRequestBody() {
        Filter = new EmployeeSearchFilter() {
            Equals = new EmployeeSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchEqualsAddress() {
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
            NotEquals = new EmployeeSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new EmployeeSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new EmployeeSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new EmployeeSearchNotEqualsAddress() {
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
            GreaterThan = new EmployeeSearchGreaterThan() {
                Meta = new EmployeeSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new EmployeeSearchSmallerThan() {
                Meta = new EmployeeSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new EmployeeSearchGreaterOrEqual() {
                Meta = new EmployeeSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new EmployeeSearchSmallerOrEqual() {
                Meta = new EmployeeSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z"),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new EmployeeSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchContainsExternal() {
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
                Address = new EmployeeSearchContainsAddress() {
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
            NotContains = new EmployeeSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new EmployeeSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new EmployeeSearchNotContainsExternal() {
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
                Address = new EmployeeSearchNotContainsAddress() {
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
            Like = new EmployeeSearchLike() {
                External = new EmployeeSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchLikeAddress() {
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
            NotLike = new EmployeeSearchNotLike() {
                External = new EmployeeSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new EmployeeSearchNotLikeAddress() {
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
            Null = new EmployeeSearchNull() {
                Meta = new EmployeeSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNullAddress() {
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
            NotNull = new EmployeeSearchNotNull() {
                Meta = new EmployeeSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new EmployeeSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new EmployeeSearchNotNullAddress() {
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

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `EmployeeSearch`                                                                                        | [EmployeeSearchRequestBody](../../Models/Components/EmployeeSearchRequestBody.md)                       | :heavy_check_mark:                                                                                      | Request body                                                                                            |                                                                                                         |
| `Limit`                                                                                                 | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The maximum number of Employees to return (default: 50) when searching Employees                        | 1                                                                                                       |
| `Offset`                                                                                                | *long*                                                                                                  | :heavy_minus_sign:                                                                                      | The number of Employees to skip before starting to return results (default: 0) when searching Employees | 0                                                                                                       |

### Response

**[Models.Requests.EmployeeSearchResponse](../../Models/Requests/EmployeeSearchResponse.md)**

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

<!-- UsageSnippet language="csharp" operationID="EmployeeGet" method="get" path="/employee/{id}" example="responseExample" -->
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

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="EmployeeUpdate" method="patch" path="/employee/{id}" example="errorExample" -->
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
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="EmployeeUpdate" method="patch" path="/employee/{id}" example="requestExample" -->
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
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="EmployeeUpdate" method="patch" path="/employee/{id}" example="responseExample" -->
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
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="EmployeeUpdate" method="patch" path="/employee/{id}" example="validationError" -->
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