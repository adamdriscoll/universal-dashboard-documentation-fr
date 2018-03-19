# [v1.5.0-beta2](https://www.powershellgallery.com/packages/UniversalDashboard/1.5.0-beta2)

**Released: 2-25-2018**

### REST API Authentication 

REST APIs now support the authentication via [JSON Web Tokens](https://jwt.io/). You can use `New-UDAuthenticationMethod` to configure JWT parameters such as Audience, Issuer and SigningKey. 

```
$AuthMethod = New-UDAuthenticationMethod -SigningKey 'SuperSecretKey'

$Server = Start-UDRestApi -Port 10001 -Endpoint @(
    New-UDEndpoint -Url "user/me" -Method "GET" -Endpoint {
        @($User) | ConvertTo-Json
    }
)-AuthenticationMethod $AuthMethod

$Token = Grant-UDJsonWebToken -UserName "Adam" -SigningKey 'SuperSecretKey' 
```

You can then use the endpoint by specifying the token via the headers parameter. 

```
$users = Invoke-RestMethod -Uri http://localhost:10001/api/user/me -Headers @{ Authorization = "Bearer $Token" }
$users | Should be "Adam"
```

You can also allow users to get tokens by authenticating through the API. Using Forms auth, you can provide an endpoint and authenticate the user how you wish. 

```
$AuthMethod = New-UDAuthenticationMethod -Endpoint {
    New-UDAuthenticationResult -Success -UserName $Credential.UserName
}

$Server = Start-UDRestApi -Port 10001 -Endpoint @(
    New-UDEndpoint -Url "user/me" -Method "GET" -Endpoint {
        @($User) | ConvertTo-Json
    }
) -AuthenticationMethod $AuthMethod
```

The user can then call the login endpoint to retrieve a token and use it against the API. 

```
$Token = Invoke-RestMethod -Uri http://localhost:10001/api/login -Method POST -Body @{ UserName = "Adam"; Password = "Test" }

$users = Invoke-RestMethod -Uri http://localhost:10001/api/user/me -Headers @{ Authorization = "Bearer $($Token.Token)" }
$users | Should be "Adam"
```

REST APIs do not support OAuth authentication. 

### GeoLocation Support

Enable GeoLocation by specifying the -GeoLocation parameter on New-UDDashboard. If a user allows the dashboard to return their location, all endpoints will have the $Location variable defined. The location variable is defined as follows: 

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

### Issues Resolved

- [\#9](https://github.com/ironmansoftware/universal-dashboard/issues/9) Custom Components for UD
- [\#10](https://github.com/ironmansoftware/universal-dashboard/issues/10) GeoLocation Support

