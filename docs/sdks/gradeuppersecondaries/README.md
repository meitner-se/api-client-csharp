# GradeUpperSecondaries

## Overview

### Available Operations

* [List](#list) - List GradeUpperSecondaries
* [Create](#create) - Create a new GradeUpperSecondary
* [Get](#get) - Get a GradeUpperSecondary
* [Delete](#delete) - Delete a GradeUpperSecondary
* [Update](#update) - Update a GradeUpperSecondary

## List

Returns a paginated list of all `GradeUpperSecondaries` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryList" method="get" path="/grade-upper-secondary" example="responseExample" -->
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

GradeUpperSecondaryListResponse? res = await sdk.GradeUpperSecondaries.ListAsync(
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

| Parameter                                                                                                                     | Type                                                                                                                          | Required                                                                                                                      | Description                                                                                                                   | Example                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `Limit`                                                                                                                       | *long*                                                                                                                        | :heavy_minus_sign:                                                                                                            | The maximum number of GradeUpperSecondaries to return (default: 50) when listing GradeUpperSecondaries                        | 1                                                                                                                             |
| `Offset`                                                                                                                      | *long*                                                                                                                        | :heavy_minus_sign:                                                                                                            | The number of GradeUpperSecondaries to skip before starting to return results (default: 0) when listing GradeUpperSecondaries | 0                                                                                                                             |

### Response

**[GradeUpperSecondaryListResponse](../../Models/Requests/GradeUpperSecondaryListResponse.md)**

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

Create a new GradeUpperSecondary

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="errorExample" -->
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

GradeUpperSecondaryCreate req = new GradeUpperSecondaryCreate() {
    External = new GradeUpperSecondaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    CourseCode = "MATMAT01a",
    LanguageCode = "SV",
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeUpperSecondaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    GradeComment = "Eleven har visat goda kunskaper i algebra.",
    Extent = GradeUpperSecondaryCreateExtent.Normal,
    SchoolYear = GradeUpperSecondaryCreateSchoolYear.Two,
    Section = GradeUpperSecondaryCreateSection.Program,
    TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
    IncludeOnFinalGrade = true,
    ProgramTitle = "Teknikprogrammet",
    StartDate = DateOnly.Parse("2024-08-19"),
    EndDate = DateOnly.Parse("2025-01-17"),
};

var res = await sdk.GradeUpperSecondaries.CreateAsync(req);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="requestExample" -->
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

GradeUpperSecondaryCreate req = new GradeUpperSecondaryCreate() {
    External = new GradeUpperSecondaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    CourseCode = "MATMAT01a",
    LanguageCode = "SV",
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeUpperSecondaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    GradeComment = "Eleven har visat goda kunskaper i algebra.",
    Extent = GradeUpperSecondaryCreateExtent.Normal,
    SchoolYear = GradeUpperSecondaryCreateSchoolYear.Two,
    Section = GradeUpperSecondaryCreateSection.Program,
    TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
    IncludeOnFinalGrade = true,
    ProgramTitle = "Teknikprogrammet",
    StartDate = DateOnly.Parse("2024-08-19"),
    EndDate = DateOnly.Parse("2025-01-17"),
};

var res = await sdk.GradeUpperSecondaries.CreateAsync(req);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="responseExample" -->
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

GradeUpperSecondaryCreate req = new GradeUpperSecondaryCreate() {
    External = new GradeUpperSecondaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    CourseCode = "MATMAT01a",
    LanguageCode = "SV",
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeUpperSecondaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    GradeComment = "Eleven har visat goda kunskaper i algebra.",
    Extent = GradeUpperSecondaryCreateExtent.Normal,
    SchoolYear = GradeUpperSecondaryCreateSchoolYear.Two,
    Section = GradeUpperSecondaryCreateSection.Program,
    TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
    IncludeOnFinalGrade = true,
    ProgramTitle = "Teknikprogrammet",
    StartDate = DateOnly.Parse("2024-08-19"),
    EndDate = DateOnly.Parse("2025-01-17"),
};

var res = await sdk.GradeUpperSecondaries.CreateAsync(req);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryCreate" method="post" path="/grade-upper-secondary" example="validationError" -->
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

GradeUpperSecondaryCreate req = new GradeUpperSecondaryCreate() {
    External = new GradeUpperSecondaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    CourseCode = "MATMAT01a",
    LanguageCode = "SV",
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeUpperSecondaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    GradeComment = "Eleven har visat goda kunskaper i algebra.",
    Extent = GradeUpperSecondaryCreateExtent.Normal,
    SchoolYear = GradeUpperSecondaryCreateSchoolYear.Two,
    Section = GradeUpperSecondaryCreateSection.Program,
    TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
    IncludeOnFinalGrade = true,
    ProgramTitle = "Teknikprogrammet",
    StartDate = DateOnly.Parse("2024-08-19"),
    EndDate = DateOnly.Parse("2025-01-17"),
};

var res = await sdk.GradeUpperSecondaries.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `request`                                                                         | [GradeUpperSecondaryCreate](../../Models/Components/GradeUpperSecondaryCreate.md) | :heavy_check_mark:                                                                | The request object to use for the request.                                        |

### Response

**[GradeUpperSecondaryCreateResponse](../../Models/Requests/GradeUpperSecondaryCreateResponse.md)**

### Errors

| Error Type                                                              | Status Code                                                             | Content Type                                                            |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                              | 400                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error401ResponseBody                              | 401                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error403ResponseBody                              | 403                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error404ResponseBody                              | 404                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error409ResponseBody                              | 409                                                                     | application/json                                                        |
| Meitner.Models.Errors.GradeUpperSecondaryCreate422ResponseBodyException | 422                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error429ResponseBody                              | 429                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error500ResponseBody                              | 500                                                                     | application/json                                                        |
| Meitner.Models.Errors.APIException                                      | 4XX, 5XX                                                                | \*/\*                                                                   |

## Get

Retrieves the `GradeUpperSecondary` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryGet" method="get" path="/grade-upper-secondary/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.GradeUpperSecondaries.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                    | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Id`                                                         | *string*                                                     | :heavy_check_mark:                                           | The unique identifier of the GradeUpperSecondary to retrieve | 123e4567-e89b-12d3-a456-426614174000                         |

### Response

**[GradeUpperSecondaryGetResponse](../../Models/Requests/GradeUpperSecondaryGetResponse.md)**

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

Delete a GradeUpperSecondary

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryDelete" method="delete" path="/grade-upper-secondary/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.GradeUpperSecondaries.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                  | Type                                                       | Required                                                   | Description                                                | Example                                                    |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `Id`                                                       | *string*                                                   | :heavy_check_mark:                                         | The unique identifier of the GradeUpperSecondary to delete | 123e4567-e89b-12d3-a456-426614174000                       |

### Response

**[GradeUpperSecondaryDeleteResponse](../../Models/Requests/GradeUpperSecondaryDeleteResponse.md)**

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

Update a GradeUpperSecondary

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="errorExample" -->
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

var res = await sdk.GradeUpperSecondaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeUpperSecondaryUpdate: new GradeUpperSecondaryUpdate() {
        External = new GradeUpperSecondaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeUpperSecondaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        GradeComment = "Eleven har visat goda kunskaper i algebra.",
        Extent = GradeUpperSecondaryUpdateExtent.Normal,
        SchoolYear = GradeUpperSecondaryUpdateSchoolYear.Two,
        Section = GradeUpperSecondaryUpdateSection.Program,
        TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
        IncludeOnFinalGrade = true,
        ProgramTitle = "Teknikprogrammet",
        StartDate = DateOnly.Parse("2024-08-19"),
        EndDate = DateOnly.Parse("2025-01-17"),
    }
);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="requestExample" -->
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

var res = await sdk.GradeUpperSecondaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeUpperSecondaryUpdate: new GradeUpperSecondaryUpdate() {
        External = new GradeUpperSecondaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeUpperSecondaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        GradeComment = "Eleven har visat goda kunskaper i algebra.",
        Extent = GradeUpperSecondaryUpdateExtent.Normal,
        SchoolYear = GradeUpperSecondaryUpdateSchoolYear.Two,
        Section = GradeUpperSecondaryUpdateSection.Program,
        TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
        IncludeOnFinalGrade = true,
        ProgramTitle = "Teknikprogrammet",
        StartDate = DateOnly.Parse("2024-08-19"),
        EndDate = DateOnly.Parse("2025-01-17"),
    }
);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="responseExample" -->
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

var res = await sdk.GradeUpperSecondaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeUpperSecondaryUpdate: new GradeUpperSecondaryUpdate() {
        External = new GradeUpperSecondaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeUpperSecondaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        GradeComment = "Eleven har visat goda kunskaper i algebra.",
        Extent = GradeUpperSecondaryUpdateExtent.Normal,
        SchoolYear = GradeUpperSecondaryUpdateSchoolYear.Two,
        Section = GradeUpperSecondaryUpdateSection.Program,
        TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
        IncludeOnFinalGrade = true,
        ProgramTitle = "Teknikprogrammet",
        StartDate = DateOnly.Parse("2024-08-19"),
        EndDate = DateOnly.Parse("2025-01-17"),
    }
);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GradeUpperSecondaryUpdate" method="patch" path="/grade-upper-secondary/{id}" example="validationError" -->
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

var res = await sdk.GradeUpperSecondaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeUpperSecondaryUpdate: new GradeUpperSecondaryUpdate() {
        External = new GradeUpperSecondaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeUpperSecondaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        GradeComment = "Eleven har visat goda kunskaper i algebra.",
        Extent = GradeUpperSecondaryUpdateExtent.Normal,
        SchoolYear = GradeUpperSecondaryUpdateSchoolYear.Two,
        Section = GradeUpperSecondaryUpdateSection.Program,
        TeacherComment = "Eleven deltar aktivt och visar stort engagemang.",
        IncludeOnFinalGrade = true,
        ProgramTitle = "Teknikprogrammet",
        StartDate = DateOnly.Parse("2024-08-19"),
        EndDate = DateOnly.Parse("2025-01-17"),
    }
);

// handle response
```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       | Example                                                                           |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `Id`                                                                              | *string*                                                                          | :heavy_check_mark:                                                                | The unique identifier of the GradeUpperSecondary to update                        | 123e4567-e89b-12d3-a456-426614174000                                              |
| `GradeUpperSecondaryUpdate`                                                       | [GradeUpperSecondaryUpdate](../../Models/Components/GradeUpperSecondaryUpdate.md) | :heavy_check_mark:                                                                | Request body                                                                      |                                                                                   |

### Response

**[GradeUpperSecondaryUpdateResponse](../../Models/Requests/GradeUpperSecondaryUpdateResponse.md)**

### Errors

| Error Type                                                              | Status Code                                                             | Content Type                                                            |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                              | 400                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error401ResponseBody                              | 401                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error403ResponseBody                              | 403                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error404ResponseBody                              | 404                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error409ResponseBody                              | 409                                                                     | application/json                                                        |
| Meitner.Models.Errors.GradeUpperSecondaryUpdate422ResponseBodyException | 422                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error429ResponseBody                              | 429                                                                     | application/json                                                        |
| Meitner.Models.Errors.Error500ResponseBody                              | 500                                                                     | application/json                                                        |
| Meitner.Models.Errors.APIException                                      | 4XX, 5XX                                                                | \*/\*                                                                   |