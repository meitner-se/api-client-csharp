<!-- Start SDK Example Usage [usage] -->
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
<!-- End SDK Example Usage [usage] -->