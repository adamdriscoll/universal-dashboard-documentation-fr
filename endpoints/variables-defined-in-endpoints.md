# Variables Defined in Endpoints

| Name | Description | Type |
|------|-------------|------|
| $Request | Request object for an HTTP request. | [HttpRequest](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.http.httprequest?view=aspnetcore-2.0) |
| $Response | Response object for an HTTP response | [HttpResponse](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.http.HttpResponse?view=aspnetcore-2.0) |
| $Location | GeoLocation information for a user. Available when -GeoLocation is specified on New-UDDashboard. | [Location](#location) |
| $User | User name for the user that authenticated against the dashboard. Only available when authentication is used. | string |
| $Cache | Memory cache used by the dashboard server | [IMemoryCache](https://docs.microsoft.com/aspnet/core/api/microsoft.extensions.caching.memory.imemorycache) |
| $ClaimsPrinciple | The entire ClaimsPrinciple object for a user. Only available when authentication is used | [ClaimsPrinciple](https://msdn.microsoft.com/en-us/library/system.security.claims.claimsprincipal\(v=vs.110\).aspx) |

# Types available

## <a name="location"></a> Location 

```
@{
    coords = @{
         latitude, 
         longitude,
         accuracy,
         altitude,
         altitudeAccuracy
         heading,
         speed
    },
    timestamp
}

```
