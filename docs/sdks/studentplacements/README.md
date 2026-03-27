# StudentPlacements

## Overview

### Available Operations

* [List](#list) - List StudentPlacements
* [Create](#create) - Create a new StudentPlacement
* [Search](#search) - Search StudentPlacements
* [Get](#get) - Get a StudentPlacement
* [Delete](#delete) - Delete a StudentPlacement
* [Update](#update) - Update a StudentPlacement
* [Archive](#archive) - Archive a student placement
* [Restore](#restore) - Restore an archived student placement

## List

Returns a paginated list of all `StudentPlacements` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentPlacementList" method="get" path="/student-placement" example="responseExample" -->
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

StudentPlacementListResponse? res = await sdk.StudentPlacements.ListAsync(
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

| Parameter                                                                                                             | Type                                                                                                                  | Required                                                                                                              | Description                                                                                                           | Example                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                               | *long*                                                                                                                | :heavy_minus_sign:                                                                                                    | The maximum number of StudentPlacements to return (default: 50) when listing StudentPlacements                        | 1                                                                                                                     |
| `Offset`                                                                                                              | *long*                                                                                                                | :heavy_minus_sign:                                                                                                    | The number of StudentPlacements to skip before starting to return results (default: 0) when listing StudentPlacements | 0                                                                                                                     |

### Response

**[StudentPlacementListResponse](../../Models/Requests/StudentPlacementListResponse.md)**

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

Create a new StudentPlacement

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementCreate" method="post" path="/student-placement" example="errorExample" -->
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

StudentPlacementCreate req = new StudentPlacementCreate() {
    External = new StudentPlacementCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolType = StudentPlacementCreateSchoolType.Gr,
    SchoolYear = StudentPlacementCreateSchoolYear.One,
    HasChildcare = true,
    MotherTongue = "SWE",
    ModernLanguageAlternative = StudentPlacementCreateModernLanguageAlternative.En,
    ModernLanguageInSchoolChoice = "deu",
    ModernLanguageInLanguageChoice = "fra",
    StartDate = DateOnly.Parse("2024-08-01"),
    EndDate = DateOnly.Parse("2025-08-01"),
};

var res = await sdk.StudentPlacements.CreateAsync(req);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementCreate" method="post" path="/student-placement" example="requestExample" -->
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

StudentPlacementCreate req = new StudentPlacementCreate() {
    External = new StudentPlacementCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolType = StudentPlacementCreateSchoolType.Gr,
    SchoolYear = StudentPlacementCreateSchoolYear.One,
    HasChildcare = true,
    MotherTongue = "SWE",
    ModernLanguageAlternative = StudentPlacementCreateModernLanguageAlternative.En,
    ModernLanguageInSchoolChoice = "deu",
    ModernLanguageInLanguageChoice = "fra",
    StartDate = DateOnly.Parse("2024-08-01"),
    EndDate = DateOnly.Parse("2025-08-01"),
};

var res = await sdk.StudentPlacements.CreateAsync(req);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementCreate" method="post" path="/student-placement" example="responseExample" -->
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

StudentPlacementCreate req = new StudentPlacementCreate() {
    External = new StudentPlacementCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolType = StudentPlacementCreateSchoolType.Gr,
    SchoolYear = StudentPlacementCreateSchoolYear.One,
    HasChildcare = true,
    MotherTongue = "SWE",
    ModernLanguageAlternative = StudentPlacementCreateModernLanguageAlternative.En,
    ModernLanguageInSchoolChoice = "deu",
    ModernLanguageInLanguageChoice = "fra",
    StartDate = DateOnly.Parse("2024-08-01"),
    EndDate = DateOnly.Parse("2025-08-01"),
};

var res = await sdk.StudentPlacements.CreateAsync(req);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="StudentPlacementCreate" method="post" path="/student-placement" example="validationError" -->
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

StudentPlacementCreate req = new StudentPlacementCreate() {
    External = new StudentPlacementCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolType = StudentPlacementCreateSchoolType.Gr,
    SchoolYear = StudentPlacementCreateSchoolYear.One,
    HasChildcare = true,
    MotherTongue = "SWE",
    ModernLanguageAlternative = StudentPlacementCreateModernLanguageAlternative.En,
    ModernLanguageInSchoolChoice = "deu",
    ModernLanguageInLanguageChoice = "fra",
    StartDate = DateOnly.Parse("2024-08-01"),
    EndDate = DateOnly.Parse("2025-08-01"),
};

var res = await sdk.StudentPlacements.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `request`                                                                   | [StudentPlacementCreate](../../Models/Components/StudentPlacementCreate.md) | :heavy_check_mark:                                                          | The request object to use for the request.                                  |

### Response

**[StudentPlacementCreateResponse](../../Models/Requests/StudentPlacementCreateResponse.md)**

### Errors

| Error Type                                                           | Status Code                                                          | Content Type                                                         |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                           | 400                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error401ResponseBody                           | 401                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error403ResponseBody                           | 403                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error404ResponseBody                           | 404                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error409ResponseBody                           | 409                                                                  | application/json                                                     |
| Meitner.Models.Errors.StudentPlacementCreate422ResponseBodyException | 422                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error429ResponseBody                           | 429                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error500ResponseBody                           | 500                                                                  | application/json                                                     |
| Meitner.Models.Errors.APIException                                   | 4XX, 5XX                                                             | \*/\*                                                                |

## Search

Search for `StudentPlacements` with filtering capabilities.

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementSearch" method="post" path="/student-placement/_search" example="errorExample" -->
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

Models.Requests.StudentPlacementSearchResponse? res = await sdk.StudentPlacements.SearchAsync(
    studentPlacementSearch: new StudentPlacementSearchRequestBody() {
        Filter = new StudentPlacementSearchFilter() {
            Equals = new StudentPlacementSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            NotEquals = new StudentPlacementSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterThan = new StudentPlacementSearchGreaterThan() {
                Meta = new StudentPlacementSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new StudentPlacementSearchSmallerThan() {
                Meta = new StudentPlacementSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new StudentPlacementSearchGreaterOrEqual() {
                Meta = new StudentPlacementSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new StudentPlacementSearchSmallerOrEqual() {
                Meta = new StudentPlacementSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new StudentPlacementSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            NotContains = new StudentPlacementSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            Like = new StudentPlacementSearchLike() {
                External = new StudentPlacementSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            NotLike = new StudentPlacementSearchNotLike() {
                External = new StudentPlacementSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            Null = new StudentPlacementSearchNull() {
                Meta = new StudentPlacementSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
            },
            NotNull = new StudentPlacementSearchNotNull() {
                Meta = new StudentPlacementSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentPlacementSearch" method="post" path="/student-placement/_search" example="requestExample" -->
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

Models.Requests.StudentPlacementSearchResponse? res = await sdk.StudentPlacements.SearchAsync(
    studentPlacementSearch: new StudentPlacementSearchRequestBody() {
        Filter = new StudentPlacementSearchFilter() {
            Equals = new StudentPlacementSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            NotEquals = new StudentPlacementSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterThan = new StudentPlacementSearchGreaterThan() {
                Meta = new StudentPlacementSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new StudentPlacementSearchSmallerThan() {
                Meta = new StudentPlacementSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new StudentPlacementSearchGreaterOrEqual() {
                Meta = new StudentPlacementSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new StudentPlacementSearchSmallerOrEqual() {
                Meta = new StudentPlacementSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new StudentPlacementSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            NotContains = new StudentPlacementSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            Like = new StudentPlacementSearchLike() {
                External = new StudentPlacementSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            NotLike = new StudentPlacementSearchNotLike() {
                External = new StudentPlacementSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            Null = new StudentPlacementSearchNull() {
                Meta = new StudentPlacementSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
            },
            NotNull = new StudentPlacementSearchNotNull() {
                Meta = new StudentPlacementSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentPlacementSearch" method="post" path="/student-placement/_search" example="responseExample" -->
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

Models.Requests.StudentPlacementSearchResponse? res = await sdk.StudentPlacements.SearchAsync(
    studentPlacementSearch: new StudentPlacementSearchRequestBody() {
        Filter = new StudentPlacementSearchFilter() {
            Equals = new StudentPlacementSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            NotEquals = new StudentPlacementSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterThan = new StudentPlacementSearchGreaterThan() {
                Meta = new StudentPlacementSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new StudentPlacementSearchSmallerThan() {
                Meta = new StudentPlacementSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new StudentPlacementSearchGreaterOrEqual() {
                Meta = new StudentPlacementSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new StudentPlacementSearchSmallerOrEqual() {
                Meta = new StudentPlacementSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new StudentPlacementSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            NotContains = new StudentPlacementSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            Like = new StudentPlacementSearchLike() {
                External = new StudentPlacementSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            NotLike = new StudentPlacementSearchNotLike() {
                External = new StudentPlacementSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            Null = new StudentPlacementSearchNull() {
                Meta = new StudentPlacementSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
            },
            NotNull = new StudentPlacementSearchNotNull() {
                Meta = new StudentPlacementSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
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

<!-- UsageSnippet language="csharp" operationID="StudentPlacementSearch" method="post" path="/student-placement/_search" example="validationError" -->
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

Models.Requests.StudentPlacementSearchResponse? res = await sdk.StudentPlacements.SearchAsync(
    studentPlacementSearch: new StudentPlacementSearchRequestBody() {
        Filter = new StudentPlacementSearchFilter() {
            Equals = new StudentPlacementSearchEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            NotEquals = new StudentPlacementSearchNotEquals() {
                Id = "123e4567-e89b-12d3-a456-426614174000",
                Meta = new StudentPlacementSearchNotEqualsMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    CreatedBy = "123e4567-e89b-12d3-a456-426614174000",
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedBy = "123e4567-e89b-12d3-a456-426614174000",
                },
                External = new StudentPlacementSearchNotEqualsExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                StudentID = "123e4567-e89b-12d3-a456-426614174000",
                SchoolID = "123e4567-e89b-12d3-a456-426614174000",
                HasChildcare = true,
                MotherTongue = "example",
                SwedishAsSecondLanguage = true,
                MotherTongueParticipates = true,
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchiveYear = "example",
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterThan = new StudentPlacementSearchGreaterThan() {
                Meta = new StudentPlacementSearchGreaterThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerThan = new StudentPlacementSearchSmallerThan() {
                Meta = new StudentPlacementSearchSmallerThanMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            GreaterOrEqual = new StudentPlacementSearchGreaterOrEqual() {
                Meta = new StudentPlacementSearchGreaterOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            SmallerOrEqual = new StudentPlacementSearchSmallerOrEqual() {
                Meta = new StudentPlacementSearchSmallerOrEqualMeta() {
                    CreatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                    UpdatedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
                },
                StartDate = DateOnly.Parse("2024-01-15"),
                EndDate = DateOnly.Parse("2024-01-15"),
                ArchivedAt = System.DateTime.Parse("2024-01-15T10:30:00Z").ToUniversalTime(),
            },
            Contains = new StudentPlacementSearchContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            NotContains = new StudentPlacementSearchNotContains() {
                Id = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                Meta = new StudentPlacementSearchNotContainsMeta() {
                    CreatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                    UpdatedBy = new List<string>() {
                        "123e4567-e89b-12d3-a456-426614174000",
                    },
                },
                External = new StudentPlacementSearchNotContainsExternal() {
                    SourceID = new List<string>() {
                        "example",
                    },
                    Source = new List<string>() {
                        "example",
                    },
                },
                StudentID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                SchoolID = new List<string>() {
                    "123e4567-e89b-12d3-a456-426614174000",
                },
                HasChildcare = new List<bool>() {
                    true,
                },
                MotherTongue = new List<string>() {
                    "example",
                },
                SwedishAsSecondLanguage = new List<bool>() {
                    true,
                },
                MotherTongueParticipates = new List<bool>() {
                    true,
                },
                ModernLanguageInSchoolChoice = new List<string>() {
                    "example",
                },
                ModernLanguageInLanguageChoice = new List<string>() {
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
            Like = new StudentPlacementSearchLike() {
                External = new StudentPlacementSearchLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            NotLike = new StudentPlacementSearchNotLike() {
                External = new StudentPlacementSearchNotLikeExternal() {
                    SourceID = "example",
                    Source = "example",
                },
                MotherTongue = "example",
                ModernLanguageInSchoolChoice = "example",
                ModernLanguageInLanguageChoice = "example",
                ArchiveYear = "example",
            },
            Null = new StudentPlacementSearchNull() {
                Meta = new StudentPlacementSearchNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
            },
            NotNull = new StudentPlacementSearchNotNull() {
                Meta = new StudentPlacementSearchNotNullMeta() {
                    CreatedBy = true,
                    UpdatedAt = true,
                    UpdatedBy = true,
                },
                External = new StudentPlacementSearchNotNullExternal() {
                    SourceID = true,
                    Source = true,
                },
                SchoolYear = true,
                MotherTongue = true,
                ModernLanguageAlternative = true,
                ModernLanguageInSchoolChoice = true,
                ModernLanguageInLanguageChoice = true,
                EndDate = true,
                ArchiveYear = true,
                ArchivedAt = true,
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

| Parameter                                                                                                               | Type                                                                                                                    | Required                                                                                                                | Description                                                                                                             | Example                                                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `StudentPlacementSearch`                                                                                                | [StudentPlacementSearchRequestBody](../../Models/Components/StudentPlacementSearchRequestBody.md)                       | :heavy_check_mark:                                                                                                      | Request body                                                                                                            |                                                                                                                         |
| `Limit`                                                                                                                 | *long*                                                                                                                  | :heavy_minus_sign:                                                                                                      | The maximum number of StudentPlacements to return (default: 50) when searching StudentPlacements                        | 1                                                                                                                       |
| `Offset`                                                                                                                | *long*                                                                                                                  | :heavy_minus_sign:                                                                                                      | The number of StudentPlacements to skip before starting to return results (default: 0) when searching StudentPlacements | 0                                                                                                                       |

### Response

**[Models.Requests.StudentPlacementSearchResponse](../../Models/Requests/StudentPlacementSearchResponse.md)**

### Errors

| Error Type                                                           | Status Code                                                          | Content Type                                                         |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                           | 400                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error401ResponseBody                           | 401                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error403ResponseBody                           | 403                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error404ResponseBody                           | 404                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error409ResponseBody                           | 409                                                                  | application/json                                                     |
| Meitner.Models.Errors.StudentPlacementSearch422ResponseBodyException | 422                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error429ResponseBody                           | 429                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error500ResponseBody                           | 500                                                                  | application/json                                                     |
| Meitner.Models.Errors.APIException                                   | 4XX, 5XX                                                             | \*/\*                                                                |

## Get

Retrieves the `StudentPlacement` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentPlacementGet" method="get" path="/student-placement/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.StudentPlacements.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                 | Type                                                      | Required                                                  | Description                                               | Example                                                   |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `Id`                                                      | *string*                                                  | :heavy_check_mark:                                        | The unique identifier of the StudentPlacement to retrieve | 123e4567-e89b-12d3-a456-426614174000                      |

### Response

**[StudentPlacementGetResponse](../../Models/Requests/StudentPlacementGetResponse.md)**

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

Delete a StudentPlacement

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentPlacementDelete" method="delete" path="/student-placement/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.StudentPlacements.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                               | Type                                                    | Required                                                | Description                                             | Example                                                 |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `Id`                                                    | *string*                                                | :heavy_check_mark:                                      | The unique identifier of the StudentPlacement to delete | 123e4567-e89b-12d3-a456-426614174000                    |

### Response

**[StudentPlacementDeleteResponse](../../Models/Requests/StudentPlacementDeleteResponse.md)**

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

Update a StudentPlacement

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementUpdate" method="patch" path="/student-placement/{id}" example="errorExample" -->
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

var res = await sdk.StudentPlacements.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentPlacementUpdate: new StudentPlacementUpdate() {
        External = new StudentPlacementUpdateExternal() {
            SourceID = "12345678",
        },
        SchoolType = StudentPlacementUpdateSchoolType.Gr,
        SchoolYear = StudentPlacementUpdateSchoolYear.One,
        HasChildcare = true,
        MotherTongue = "SWE",
        ModernLanguageAlternative = StudentPlacementUpdateModernLanguageAlternative.En,
        ModernLanguageInSchoolChoice = "deu",
        ModernLanguageInLanguageChoice = "fra",
        StartDate = DateOnly.Parse("2024-08-01"),
        EndDate = DateOnly.Parse("2025-08-01"),
    }
);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementUpdate" method="patch" path="/student-placement/{id}" example="requestExample" -->
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

var res = await sdk.StudentPlacements.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentPlacementUpdate: new StudentPlacementUpdate() {
        External = new StudentPlacementUpdateExternal() {
            SourceID = "12345678",
        },
        SchoolType = StudentPlacementUpdateSchoolType.Gr,
        SchoolYear = StudentPlacementUpdateSchoolYear.One,
        HasChildcare = true,
        MotherTongue = "SWE",
        ModernLanguageAlternative = StudentPlacementUpdateModernLanguageAlternative.En,
        ModernLanguageInSchoolChoice = "deu",
        ModernLanguageInLanguageChoice = "fra",
        StartDate = DateOnly.Parse("2024-08-01"),
        EndDate = DateOnly.Parse("2025-08-01"),
    }
);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="StudentPlacementUpdate" method="patch" path="/student-placement/{id}" example="responseExample" -->
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

var res = await sdk.StudentPlacements.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentPlacementUpdate: new StudentPlacementUpdate() {
        External = new StudentPlacementUpdateExternal() {
            SourceID = "12345678",
        },
        SchoolType = StudentPlacementUpdateSchoolType.Gr,
        SchoolYear = StudentPlacementUpdateSchoolYear.One,
        HasChildcare = true,
        MotherTongue = "SWE",
        ModernLanguageAlternative = StudentPlacementUpdateModernLanguageAlternative.En,
        ModernLanguageInSchoolChoice = "deu",
        ModernLanguageInLanguageChoice = "fra",
        StartDate = DateOnly.Parse("2024-08-01"),
        EndDate = DateOnly.Parse("2025-08-01"),
    }
);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="StudentPlacementUpdate" method="patch" path="/student-placement/{id}" example="validationError" -->
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

var res = await sdk.StudentPlacements.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    studentPlacementUpdate: new StudentPlacementUpdate() {
        External = new StudentPlacementUpdateExternal() {
            SourceID = "12345678",
        },
        SchoolType = StudentPlacementUpdateSchoolType.Gr,
        SchoolYear = StudentPlacementUpdateSchoolYear.One,
        HasChildcare = true,
        MotherTongue = "SWE",
        ModernLanguageAlternative = StudentPlacementUpdateModernLanguageAlternative.En,
        ModernLanguageInSchoolChoice = "deu",
        ModernLanguageInLanguageChoice = "fra",
        StartDate = DateOnly.Parse("2024-08-01"),
        EndDate = DateOnly.Parse("2025-08-01"),
    }
);

// handle response
```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 | Example                                                                     |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `Id`                                                                        | *string*                                                                    | :heavy_check_mark:                                                          | The unique identifier of the StudentPlacement to update                     | 123e4567-e89b-12d3-a456-426614174000                                        |
| `StudentPlacementUpdate`                                                    | [StudentPlacementUpdate](../../Models/Components/StudentPlacementUpdate.md) | :heavy_check_mark:                                                          | Request body                                                                |                                                                             |

### Response

**[StudentPlacementUpdateResponse](../../Models/Requests/StudentPlacementUpdateResponse.md)**

### Errors

| Error Type                                                           | Status Code                                                          | Content Type                                                         |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                           | 400                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error401ResponseBody                           | 401                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error403ResponseBody                           | 403                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error404ResponseBody                           | 404                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error409ResponseBody                           | 409                                                                  | application/json                                                     |
| Meitner.Models.Errors.StudentPlacementUpdate422ResponseBodyException | 422                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error429ResponseBody                           | 429                                                                  | application/json                                                     |
| Meitner.Models.Errors.Error500ResponseBody                           | 500                                                                  | application/json                                                     |
| Meitner.Models.Errors.APIException                                   | 4XX, 5XX                                                             | \*/\*                                                                |

## Archive

Archive a student placement.

**Recommended usage:**
We recommend only archiving student placements that have a passed end date. When building syncs from external systems and a studentPlacement is removed, we recommend the following workflow:

1. Set the `endDate` to the date when the studentPlacement was removed from the external system
2. Wait approximately 5 days before archiving the student placement

This grace period allows time to correct any mistakes made by administrators in the external system before the placement is permanently archived.


### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentPlacementArchive" method="patch" path="/student-placement/{id}/archive" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.StudentPlacements.ArchiveAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `Id`                                       | *string*                                   | :heavy_check_mark:                         | The ID of the student placement to archive | 123e4567-e89b-12d3-a456-426614174000       |

### Response

**[StudentPlacementArchiveResponse](../../Models/Requests/StudentPlacementArchiveResponse.md)**

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

## Restore

Restore an archived student placement

### Example Usage

<!-- UsageSnippet language="csharp" operationID="StudentPlacementRestore" method="patch" path="/student-placement/{id}/restore" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.StudentPlacements.RestoreAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                | Example                                    |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `Id`                                       | *string*                                   | :heavy_check_mark:                         | The ID of the student placement to restore | 123e4567-e89b-12d3-a456-426614174000       |

### Response

**[StudentPlacementRestoreResponse](../../Models/Requests/StudentPlacementRestoreResponse.md)**

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