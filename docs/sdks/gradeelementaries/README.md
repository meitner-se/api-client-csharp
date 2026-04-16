# GradeElementaries

## Overview

### Available Operations

* [List](#list) - List GradeElementaries
* [Create](#create) - Create a new GradeElementary
* [Get](#get) - Get a GradeElementary
* [Delete](#delete) - Delete a GradeElementary
* [Update](#update) - Update a GradeElementary

## List

Returns a paginated list of all `GradeElementaries` in your organization.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeElementaryList" method="get" path="/grade-elementary" example="responseExample" -->
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

GradeElementaryListResponse? res = await sdk.GradeElementaries.ListAsync(
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
| `Limit`                                                                                                               | *long*                                                                                                                | :heavy_minus_sign:                                                                                                    | The maximum number of GradeElementaries to return (default: 50) when listing GradeElementaries                        | 1                                                                                                                     |
| `Offset`                                                                                                              | *long*                                                                                                                | :heavy_minus_sign:                                                                                                    | The number of GradeElementaries to skip before starting to return results (default: 0) when listing GradeElementaries | 0                                                                                                                     |

### Response

**[GradeElementaryListResponse](../../Models/Requests/GradeElementaryListResponse.md)**

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

Create a new GradeElementary

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="errorExample" -->
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

GradeElementaryCreate req = new GradeElementaryCreate() {
    External = new GradeElementaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SubjectCode = "MA",
    LanguageCode = "SV",
    AcademicYear = "2024/2025",
    Term = GradeElementaryCreateTerm.Ht,
    SchoolYear = GradeElementaryCreateSchoolYear.Nine,
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeElementaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    FinalGrade = true,
    IsEnded = true,
    SchoolComment = "Utmärkt arbete under hela terminen.",
};

var res = await sdk.GradeElementaries.CreateAsync(req);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="requestExample" -->
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

GradeElementaryCreate req = new GradeElementaryCreate() {
    External = new GradeElementaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SubjectCode = "MA",
    LanguageCode = "SV",
    AcademicYear = "2024/2025",
    Term = GradeElementaryCreateTerm.Ht,
    SchoolYear = GradeElementaryCreateSchoolYear.Nine,
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeElementaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    FinalGrade = true,
    IsEnded = true,
    SchoolComment = "Utmärkt arbete under hela terminen.",
};

var res = await sdk.GradeElementaries.CreateAsync(req);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="responseExample" -->
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

GradeElementaryCreate req = new GradeElementaryCreate() {
    External = new GradeElementaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SubjectCode = "MA",
    LanguageCode = "SV",
    AcademicYear = "2024/2025",
    Term = GradeElementaryCreateTerm.Ht,
    SchoolYear = GradeElementaryCreateSchoolYear.Nine,
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeElementaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    FinalGrade = true,
    IsEnded = true,
    SchoolComment = "Utmärkt arbete under hela terminen.",
};

var res = await sdk.GradeElementaries.CreateAsync(req);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GradeElementaryCreate" method="post" path="/grade-elementary" example="validationError" -->
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

GradeElementaryCreate req = new GradeElementaryCreate() {
    External = new GradeElementaryCreateExternal() {
        SourceID = "12345678",
    },
    StudentID = "123e4567-e89b-12d3-a456-426614174000",
    SchoolID = "123e4567-e89b-12d3-a456-426614174000",
    SubjectCode = "MA",
    LanguageCode = "SV",
    AcademicYear = "2024/2025",
    Term = GradeElementaryCreateTerm.Ht,
    SchoolYear = GradeElementaryCreateSchoolYear.Nine,
    Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
    Grade = GradeElementaryCreateGrade.A,
    GradeDate = DateOnly.Parse("2025-01-15"),
    FinalGrade = true,
    IsEnded = true,
    SchoolComment = "Utmärkt arbete under hela terminen.",
};

var res = await sdk.GradeElementaries.CreateAsync(req);

// handle response
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `request`                                                                 | [GradeElementaryCreate](../../Models/Components/GradeElementaryCreate.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |

### Response

**[GradeElementaryCreateResponse](../../Models/Requests/GradeElementaryCreateResponse.md)**

### Errors

| Error Type                                                          | Status Code                                                         | Content Type                                                        |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                          | 400                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error401ResponseBody                          | 401                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error403ResponseBody                          | 403                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error404ResponseBody                          | 404                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error409ResponseBody                          | 409                                                                 | application/json                                                    |
| Meitner.Models.Errors.GradeElementaryCreate422ResponseBodyException | 422                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error429ResponseBody                          | 429                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error500ResponseBody                          | 500                                                                 | application/json                                                    |
| Meitner.Models.Errors.APIException                                  | 4XX, 5XX                                                            | \*/\*                                                               |

## Get

Retrieves the `GradeElementary` with the given ID.

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeElementaryGet" method="get" path="/grade-elementary/{id}" example="responseExample" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.GradeElementaries.GetAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `Id`                                                     | *string*                                                 | :heavy_check_mark:                                       | The unique identifier of the GradeElementary to retrieve | 123e4567-e89b-12d3-a456-426614174000                     |

### Response

**[GradeElementaryGetResponse](../../Models/Requests/GradeElementaryGetResponse.md)**

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

Delete a GradeElementary

### Example Usage

<!-- UsageSnippet language="csharp" operationID="GradeElementaryDelete" method="delete" path="/grade-elementary/{id}" -->
```csharp
using Meitner;
using Meitner.Models.Components;

var sdk = new MeitnerSDK(security: new Security() {
    Option1 = new SecurityOption1() {
        ClientCredentials = "<YOUR_API_KEY_HERE>",
        ClientSecret = "<YOUR_API_KEY_HERE>",
    },
});

var res = await sdk.GradeElementaries.DeleteAsync(id: "123e4567-e89b-12d3-a456-426614174000");

// handle response
```

### Parameters

| Parameter                                              | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `Id`                                                   | *string*                                               | :heavy_check_mark:                                     | The unique identifier of the GradeElementary to delete | 123e4567-e89b-12d3-a456-426614174000                   |

### Response

**[GradeElementaryDeleteResponse](../../Models/Requests/GradeElementaryDeleteResponse.md)**

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

Update a GradeElementary

### Example Usage: errorExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="errorExample" -->
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

var res = await sdk.GradeElementaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeElementaryUpdate: new GradeElementaryUpdate() {
        External = new GradeElementaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        AcademicYear = "2024/2025",
        Term = GradeElementaryUpdateTerm.Ht,
        SchoolYear = GradeElementaryUpdateSchoolYear.Nine,
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeElementaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        FinalGrade = true,
        IsEnded = true,
        SchoolComment = "Utmärkt arbete under hela terminen.",
    }
);

// handle response
```
### Example Usage: requestExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="requestExample" -->
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

var res = await sdk.GradeElementaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeElementaryUpdate: new GradeElementaryUpdate() {
        External = new GradeElementaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        AcademicYear = "2024/2025",
        Term = GradeElementaryUpdateTerm.Ht,
        SchoolYear = GradeElementaryUpdateSchoolYear.Nine,
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeElementaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        FinalGrade = true,
        IsEnded = true,
        SchoolComment = "Utmärkt arbete under hela terminen.",
    }
);

// handle response
```
### Example Usage: responseExample

<!-- UsageSnippet language="csharp" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="responseExample" -->
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

var res = await sdk.GradeElementaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeElementaryUpdate: new GradeElementaryUpdate() {
        External = new GradeElementaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        AcademicYear = "2024/2025",
        Term = GradeElementaryUpdateTerm.Ht,
        SchoolYear = GradeElementaryUpdateSchoolYear.Nine,
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeElementaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        FinalGrade = true,
        IsEnded = true,
        SchoolComment = "Utmärkt arbete under hela terminen.",
    }
);

// handle response
```
### Example Usage: validationError

<!-- UsageSnippet language="csharp" operationID="GradeElementaryUpdate" method="patch" path="/grade-elementary/{id}" example="validationError" -->
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

var res = await sdk.GradeElementaries.UpdateAsync(
    id: "123e4567-e89b-12d3-a456-426614174000",
    gradeElementaryUpdate: new GradeElementaryUpdate() {
        External = new GradeElementaryUpdateExternal() {
            SourceID = "12345678",
        },
        LanguageCode = "SV",
        AcademicYear = "2024/2025",
        Term = GradeElementaryUpdateTerm.Ht,
        SchoolYear = GradeElementaryUpdateSchoolYear.Nine,
        Teacher1EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Teacher2EmployeeID = "123e4567-e89b-12d3-a456-426614174000",
        Grade = GradeElementaryUpdateGrade.A,
        GradeDate = DateOnly.Parse("2025-01-15"),
        FinalGrade = true,
        IsEnded = true,
        SchoolComment = "Utmärkt arbete under hela terminen.",
    }
);

// handle response
```

### Parameters

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               | Example                                                                   |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `Id`                                                                      | *string*                                                                  | :heavy_check_mark:                                                        | The unique identifier of the GradeElementary to update                    | 123e4567-e89b-12d3-a456-426614174000                                      |
| `GradeElementaryUpdate`                                                   | [GradeElementaryUpdate](../../Models/Components/GradeElementaryUpdate.md) | :heavy_check_mark:                                                        | Request body                                                              |                                                                           |

### Response

**[GradeElementaryUpdateResponse](../../Models/Requests/GradeElementaryUpdateResponse.md)**

### Errors

| Error Type                                                          | Status Code                                                         | Content Type                                                        |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Meitner.Models.Errors.Error400ResponseBody                          | 400                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error401ResponseBody                          | 401                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error403ResponseBody                          | 403                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error404ResponseBody                          | 404                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error409ResponseBody                          | 409                                                                 | application/json                                                    |
| Meitner.Models.Errors.GradeElementaryUpdate422ResponseBodyException | 422                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error429ResponseBody                          | 429                                                                 | application/json                                                    |
| Meitner.Models.Errors.Error500ResponseBody                          | 500                                                                 | application/json                                                    |
| Meitner.Models.Errors.APIException                                  | 4XX, 5XX                                                            | \*/\*                                                               |