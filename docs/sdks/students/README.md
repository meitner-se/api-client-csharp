# Students

## Overview

### Available Operations

* [List](#list) - List Students
* [Create](#create) - Create a new Student
* [Search](#search) - Search Students
* [Get](#get) - Get a Student
* [Delete](#delete) - Delete a Student
* [Update](#update) - Update a Student

## List

Returns a paginated list of all `Students` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentList" method="get" path="/student" example="responseExample" -->
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

StudentListResponse? res = await sdk.Students.ListAsync(
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

| Parameter                                                                                           | Type                                                                                                | Required                                                                                            | Description                                                                                         | Example                                                                                             |
| --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                             | *long*                                                                                              | :heavy_minus_sign:                                                                                  | The maximum number of Students to return (default: 50) when listing Students                        | 1                                                                                                   |
| `Offset`                                                                                            | *long*                                                                                              | :heavy_minus_sign:                                                                                  | The number of Students to skip before starting to return results (default: 0) when listing Students | 0                                                                                                   |

### Response

**[StudentListResponse](../../Models/Requests/StudentListResponse.md)**

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

Create a new Student

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentCreate" method="post" path="/student" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

StudentCreate req = new StudentCreate() {
    External = new StudentCreateExternal() {
        SourceID = "12345678",
    },
    Gender = StudentCreateGender.Female,
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    DateOfBirth = DateOnly.Parse("2019-12-16"),
    Address = new StudentCreateAddress() {
        PostalAddress = "Dalvägen 14",
        PostalCode = "169 56",
        PostalCity = "Solna",
        CountryCode = "SWE",
        MunicipalityCode = "0184",
    },
    EmailAddress1 = "lise@meitner.se",
    EmailAddress2 = "lise@gmail.com",
    PhoneNumber1 = "+46701234567",
    PhoneNumber2 = "example",
    EduPersonPrincipalName = "kalko@edu.goteborg.se",
};

var res = await sdk.Students.CreateAsync(req);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="StudentCreate" method="post" path="/student" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

StudentCreate req = new StudentCreate() {
    External = new StudentCreateExternal() {
        SourceID = "12345678",
    },
    Gender = StudentCreateGender.Female,
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    DateOfBirth = DateOnly.Parse("2019-12-16"),
    Address = new StudentCreateAddress() {
        PostalAddress = "Dalvägen 14",
        PostalCode = "169 56",
        PostalCity = "Solna",
        CountryCode = "SWE",
        MunicipalityCode = "0184",
    },
    EmailAddress1 = "lise@meitner.se",
    EmailAddress2 = "lise@gmail.com",
    PhoneNumber1 = "+46701234567",
    PhoneNumber2 = "example",
    EduPersonPrincipalName = "kalko@edu.goteborg.se",
};

var res = await sdk.Students.CreateAsync(req);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="StudentCreate" method="post" path="/student" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

StudentCreate req = new StudentCreate() {
    External = new StudentCreateExternal() {
        SourceID = "12345678",
    },
    Gender = StudentCreateGender.Female,
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    DateOfBirth = DateOnly.Parse("2019-12-16"),
    Address = new StudentCreateAddress() {
        PostalAddress = "Dalvägen 14",
        PostalCode = "169 56",
        PostalCity = "Solna",
        CountryCode = "SWE",
        MunicipalityCode = "0184",
    },
    EmailAddress1 = "lise@meitner.se",
    EmailAddress2 = "lise@gmail.com",
    PhoneNumber1 = "+46701234567",
    PhoneNumber2 = "example",
    EduPersonPrincipalName = "kalko@edu.goteborg.se",
};

var res = await sdk.Students.CreateAsync(req);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="StudentCreate" method="post" path="/student" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

StudentCreate req = new StudentCreate() {
    External = new StudentCreateExternal() {
        SourceID = "12345678",
    },
    Gender = StudentCreateGender.Female,
    IdentityNumber = "20191216-1234",
    IdentityTemporary = true,
    FirstName = "Lise",
    LastName = "Meitner",
    DateOfBirth = DateOnly.Parse("2019-12-16"),
    Address = new StudentCreateAddress() {
        PostalAddress = "Dalvägen 14",
        PostalCode = "169 56",
        PostalCity = "Solna",
        CountryCode = "SWE",
        MunicipalityCode = "0184",
    },
    EmailAddress1 = "lise@meitner.se",
    EmailAddress2 = "lise@gmail.com",
    PhoneNumber1 = "+46701234567",
    PhoneNumber2 = "example",
    EduPersonPrincipalName = "kalko@edu.goteborg.se",
};

var res = await sdk.Students.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `request`                                                 | [StudentCreate](../../Models/Components/StudentCreate.md) | :heavy_check_mark:                                        | The request object to use for the request.                |

### Response

**[StudentCreateResponse](../../Models/Requests/StudentCreateResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                  | 400                                                         | application/json                                            |
| Meitner.Models.Errors.Error401ResponseBody                  | 401                                                         | application/json                                            |
| Meitner.Models.Errors.Error403ResponseBody                  | 403                                                         | application/json                                            |
| Meitner.Models.Errors.Error404ResponseBody                  | 404                                                         | application/json                                            |
| Meitner.Models.Errors.Error409ResponseBody                  | 409                                                         | application/json                                            |
| Meitner.Models.Errors.StudentCreate422ResponseBodyException | 422                                                         | application/json                                            |
| Meitner.Models.Errors.Error429ResponseBody                  | 429                                                         | application/json                                            |
| Meitner.Models.Errors.Error500ResponseBody                  | 500                                                         | application/json                                            |
| Meitner.Models.Errors.APIException                          | 4XX, 5XX                                                    | \*/\*                                                       |

## Search

Search for `Students` with filtering capabilities.

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentSearch" method="post" path="/student/_search" example="errorExample" -->
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

Models.Requests.StudentSearchResponse? res = await sdk.Students.SearchAsync(
    studentSearch: new StudentSearchRequestBody() {
        Filter = new StudentSearchFilter() {
            Equals = new StudentSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotEquals = new StudentSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchNotEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            GreaterThan = new StudentSearchGreaterThan() {
                Meta = new StudentSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new StudentSearchSmallerThan() {
                Meta = new StudentSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new StudentSearchGreaterOrEqual() {
                Meta = new StudentSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new StudentSearchSmallerOrEqual() {
                Meta = new StudentSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new StudentSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchContainsExternal() {
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
                Address = new StudentSearchContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            NotContains = new StudentSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchNotContainsExternal() {
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
                Address = new StudentSearchNotContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            Like = new StudentSearchLike() {
                External = new StudentSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotLike = new StudentSearchNotLike() {
                External = new StudentSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchNotLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            Null = new StudentSearchNull() {
                Meta = new StudentSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNullAddress() {
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
                EduPersonPrincipalName = true,
            },
            NotNull = new StudentSearchNotNull() {
                Meta = new StudentSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNotNullAddress() {
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
                EduPersonPrincipalName = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentSearch" method="post" path="/student/_search" example="requestExample" -->
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

Models.Requests.StudentSearchResponse? res = await sdk.Students.SearchAsync(
    studentSearch: new StudentSearchRequestBody() {
        Filter = new StudentSearchFilter() {
            Equals = new StudentSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotEquals = new StudentSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchNotEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            GreaterThan = new StudentSearchGreaterThan() {
                Meta = new StudentSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new StudentSearchSmallerThan() {
                Meta = new StudentSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new StudentSearchGreaterOrEqual() {
                Meta = new StudentSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new StudentSearchSmallerOrEqual() {
                Meta = new StudentSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new StudentSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchContainsExternal() {
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
                Address = new StudentSearchContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            NotContains = new StudentSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchNotContainsExternal() {
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
                Address = new StudentSearchNotContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            Like = new StudentSearchLike() {
                External = new StudentSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotLike = new StudentSearchNotLike() {
                External = new StudentSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchNotLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            Null = new StudentSearchNull() {
                Meta = new StudentSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNullAddress() {
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
                EduPersonPrincipalName = true,
            },
            NotNull = new StudentSearchNotNull() {
                Meta = new StudentSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNotNullAddress() {
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
                EduPersonPrincipalName = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentSearch" method="post" path="/student/_search" example="responseExample" -->
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

Models.Requests.StudentSearchResponse? res = await sdk.Students.SearchAsync(
    studentSearch: new StudentSearchRequestBody() {
        Filter = new StudentSearchFilter() {
            Equals = new StudentSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotEquals = new StudentSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchNotEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            GreaterThan = new StudentSearchGreaterThan() {
                Meta = new StudentSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new StudentSearchSmallerThan() {
                Meta = new StudentSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new StudentSearchGreaterOrEqual() {
                Meta = new StudentSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new StudentSearchSmallerOrEqual() {
                Meta = new StudentSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new StudentSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchContainsExternal() {
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
                Address = new StudentSearchContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            NotContains = new StudentSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchNotContainsExternal() {
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
                Address = new StudentSearchNotContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            Like = new StudentSearchLike() {
                External = new StudentSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotLike = new StudentSearchNotLike() {
                External = new StudentSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchNotLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            Null = new StudentSearchNull() {
                Meta = new StudentSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNullAddress() {
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
                EduPersonPrincipalName = true,
            },
            NotNull = new StudentSearchNotNull() {
                Meta = new StudentSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNotNullAddress() {
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
                EduPersonPrincipalName = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentSearch" method="post" path="/student/_search" example="validationError" -->
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

Models.Requests.StudentSearchResponse? res = await sdk.Students.SearchAsync(
    studentSearch: new StudentSearchRequestBody() {
        Filter = new StudentSearchFilter() {
            Equals = new StudentSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotEquals = new StudentSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                IdentityTemporary = true,
                FirstName = "example",
                LastName = "example",
                DateOfBirth = DateOnly.Parse("2024-01-15"),
                Address = new StudentSearchNotEqualsAddress() {
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
                EduPersonPrincipalName = "example",
            },
            GreaterThan = new StudentSearchGreaterThan() {
                Meta = new StudentSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerThan = new StudentSearchSmallerThan() {
                Meta = new StudentSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            GreaterOrEqual = new StudentSearchGreaterOrEqual() {
                Meta = new StudentSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            SmallerOrEqual = new StudentSearchSmallerOrEqual() {
                Meta = new StudentSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                DateOfBirth = DateOnly.Parse("2024-01-15"),
            },
            Contains = new StudentSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchContainsExternal() {
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
                Address = new StudentSearchContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            NotContains = new StudentSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentSearchNotContainsExternal() {
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
                Address = new StudentSearchNotContainsAddress() {
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
                EduPersonPrincipalName = new List<string>() {
                    "example",
                },
            },
            Like = new StudentSearchLike() {
                External = new StudentSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            NotLike = new StudentSearchNotLike() {
                External = new StudentSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                IdentityNumber = "example",
                FirstName = "example",
                LastName = "example",
                Address = new StudentSearchNotLikeAddress() {
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
                EduPersonPrincipalName = "example",
            },
            Null = new StudentSearchNull() {
                Meta = new StudentSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNullAddress() {
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
                EduPersonPrincipalName = true,
            },
            NotNull = new StudentSearchNotNull() {
                Meta = new StudentSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                Gender = true,
                DateOfBirth = true,
                Address = new StudentSearchNotNullAddress() {
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
                EduPersonPrincipalName = true,
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

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           | Example                                                                                               |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `StudentSearch`                                                                                       | [StudentSearchRequestBody](../../Models/Components/StudentSearchRequestBody.md)                       | :heavy_check_mark:                                                                                    | Request body                                                                                          |                                                                                                       |
| `Limit`                                                                                               | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The maximum number of Students to return (default: 50) when searching Students                        | 1                                                                                                     |
| `Offset`                                                                                              | *long*                                                                                                | :heavy_minus_sign:                                                                                    | The number of Students to skip before starting to return results (default: 0) when searching Students | 0                                                                                                     |

### Response

**[Models.Requests.StudentSearchResponse](../../Models/Requests/StudentSearchResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                  | 400                                                         | application/json                                            |
| Meitner.Models.Errors.Error401ResponseBody                  | 401                                                         | application/json                                            |
| Meitner.Models.Errors.Error403ResponseBody                  | 403                                                         | application/json                                            |
| Meitner.Models.Errors.Error404ResponseBody                  | 404                                                         | application/json                                            |
| Meitner.Models.Errors.Error409ResponseBody                  | 409                                                         | application/json                                            |
| Meitner.Models.Errors.StudentSearch422ResponseBodyException | 422                                                         | application/json                                            |
| Meitner.Models.Errors.Error429ResponseBody                  | 429                                                         | application/json                                            |
| Meitner.Models.Errors.Error500ResponseBody                  | 500                                                         | application/json                                            |
| Meitner.Models.Errors.APIException                          | 4XX, 5XX                                                    | \*/\*                                                       |

## Get

Retrieves the `Student` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentGet" method="get" path="/student/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                        | Type                                             | Required                                         | Description                                      | Example                                          |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `Id`                                             | *string*                                         | :heavy_check_mark:                               | The unique identifier of the Student to retrieve | 123e4567-e89b-12d3-a456-426614174000             |

### Response

**[StudentGetResponse](../../Models/Requests/StudentGetResponse.md)**

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

Delete a Student

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentDelete" method="delete" path="/student/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                      | Type                                           | Required                                       | Description                                    | Example                                        |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `Id`                                           | *string*                                       | :heavy_check_mark:                             | The unique identifier of the Student to delete | 123e4567-e89b-12d3-a456-426614174000           |

### Response

**[StudentDeleteResponse](../../Models/Requests/StudentDeleteResponse.md)**

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

Update a Student

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentUpdate" method="patch" path="/student/{id}" example="errorExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentUpdate: new StudentUpdate() {
        External = new StudentUpdateExternal() {
            SourceID = "12345678",
        },
        Gender = StudentUpdateGender.Female,
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        DateOfBirth = DateOnly.Parse("2019-12-16"),
        Address = new StudentUpdateAddress() {
            PostalAddress = "Dalvägen 14",
            PostalCode = "169 56",
            PostalCity = "Solna",
            CountryCode = "SWE",
            MunicipalityCode = "0184",
        },
        EmailAddress1 = "lise@meitner.se",
        EmailAddress2 = "lise@gmail.com",
        PhoneNumber1 = "+46701234567",
        PhoneNumber2 = "example",
        EduPersonPrincipalName = "kalko@edu.goteborg.se",
    }
);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="StudentUpdate" method="patch" path="/student/{id}" example="requestExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentUpdate: new StudentUpdate() {
        External = new StudentUpdateExternal() {
            SourceID = "12345678",
        },
        Gender = StudentUpdateGender.Female,
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        DateOfBirth = DateOnly.Parse("2019-12-16"),
        Address = new StudentUpdateAddress() {
            PostalAddress = "Dalvägen 14",
            PostalCode = "169 56",
            PostalCity = "Solna",
            CountryCode = "SWE",
            MunicipalityCode = "0184",
        },
        EmailAddress1 = "lise@meitner.se",
        EmailAddress2 = "lise@gmail.com",
        PhoneNumber1 = "+46701234567",
        PhoneNumber2 = "example",
        EduPersonPrincipalName = "kalko@edu.goteborg.se",
    }
);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="StudentUpdate" method="patch" path="/student/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentUpdate: new StudentUpdate() {
        External = new StudentUpdateExternal() {
            SourceID = "12345678",
        },
        Gender = StudentUpdateGender.Female,
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        DateOfBirth = DateOnly.Parse("2019-12-16"),
        Address = new StudentUpdateAddress() {
            PostalAddress = "Dalvägen 14",
            PostalCode = "169 56",
            PostalCity = "Solna",
            CountryCode = "SWE",
            MunicipalityCode = "0184",
        },
        EmailAddress1 = "lise@meitner.se",
        EmailAddress2 = "lise@gmail.com",
        PhoneNumber1 = "+46701234567",
        PhoneNumber2 = "example",
        EduPersonPrincipalName = "kalko@edu.goteborg.se",
    }
);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="StudentUpdate" method="patch" path="/student/{id}" example="validationError" -->
```csharp
using Meitner;
using Meitner.Models.Components;
using System;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.Students.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentUpdate: new StudentUpdate() {
        External = new StudentUpdateExternal() {
            SourceID = "12345678",
        },
        Gender = StudentUpdateGender.Female,
        IdentityNumber = "20191216-1234",
        IdentityTemporary = true,
        FirstName = "Lise",
        LastName = "Meitner",
        DateOfBirth = DateOnly.Parse("2019-12-16"),
        Address = new StudentUpdateAddress() {
            PostalAddress = "Dalvägen 14",
            PostalCode = "169 56",
            PostalCity = "Solna",
            CountryCode = "SWE",
            MunicipalityCode = "0184",
        },
        EmailAddress1 = "lise@meitner.se",
        EmailAddress2 = "lise@gmail.com",
        PhoneNumber1 = "+46701234567",
        PhoneNumber2 = "example",
        EduPersonPrincipalName = "kalko@edu.goteborg.se",
    }
);

// handle response
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               | Example                                                   |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `Id`                                                      | *string*                                                  | :heavy_check_mark:                                        | The unique identifier of the Student to update            | 123e4567-e89b-12d3-a456-426614174000                      |
| `StudentUpdate`                                           | [StudentUpdate](../../Models/Components/StudentUpdate.md) | :heavy_check_mark:                                        | Request body                                              |                                                           |

### Response

**[StudentUpdateResponse](../../Models/Requests/StudentUpdateResponse.md)**

### Errors

| Error Type                                                  | Status Code                                                 | Content Type                                                |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                  | 400                                                         | application/json                                            |
| Meitner.Models.Errors.Error401ResponseBody                  | 401                                                         | application/json                                            |
| Meitner.Models.Errors.Error403ResponseBody                  | 403                                                         | application/json                                            |
| Meitner.Models.Errors.Error404ResponseBody                  | 404                                                         | application/json                                            |
| Meitner.Models.Errors.Error409ResponseBody                  | 409                                                         | application/json                                            |
| Meitner.Models.Errors.StudentUpdate422ResponseBodyException | 422                                                         | application/json                                            |
| Meitner.Models.Errors.Error429ResponseBody                  | 429                                                         | application/json                                            |
| Meitner.Models.Errors.Error500ResponseBody                  | 500                                                         | application/json                                            |
| Meitner.Models.Errors.APIException                          | 4XX, 5XX                                                    | \*/\*                                                       |