# [v1.6.0-beta1](https://www.powershellgallery.com/packages/UniversalDashboard/1.6.0-beta1)

**Released: April 18th, 2018**

## Open Source Controls

This release of Universal Dashboard adds **20** new controls. These controls are primarily basics like buttons, checkboxes and headers but also include some bling like modules and preloaders.

All of these controls are built with `New-UDElement` and are open source on [GitHub](https://github.com/ironmansoftware/ud-controls). In addition to the controls, there is also a demo that provides examples.

## Scheduled Endpoints

With scheduled endpoints you can now collect data on an interval. It's easy to specify intervals of seconds, minutes, hours and days. If you want to get fancy, you can also specify a CRON schedule.

Scheduled endpoints are great for collecting data from all your servers and storing it within the Universal Dashboard cache or in a database.

```
$Schedule = New-UDEndpointSchedule -Every 1 -Second 

$EverySecond = New-UDEndpoint -Schedule $Schedule -Endpoint {
    $Cache:ModuleCount = (Get-Module -ListAvailable).Count
}
```

## Cache Variable Scope

Cached variables are stored in the ASP.NET memory cache. This allows you to access those variables in any endpoint. This will greatly improve the performance of your dashboards. Use scheduled endpoints to grab performance data from servers and then display data in charts for optimal speed.

```
$CachedModuleCount = New-UDEndpoint -Url "/cached-moduleCount" -Endpoint {
    $Cache:ModuleCount
}
```

## Session Variable Scope

Like cached variables, Session variables use a new scope. Session variables store data that is available per session. This is helpful when developing web forms that require user input. You wouldn't want to share this data between sessions but want to be able to access that data in between endpoints for a particular user.

One great advantage of this would be to create dashboards that allow the user to change values that in turn update the charts and counters on the page.

```
New-UDCheckbox -Label "Wax on" -OnChange {
    $Session:WaxOn = $EventData
}

 New-UDCounter -Title "Wax on\Wax Off" -Endpoint {
    if ($Session:WaxOn) {
        1
    } else {
        0   
    }
}
```

## Issues Resolved

* [\#14](https://github.com/ironmansoftware/universal-dashboard/issues/14) - New-UDGrid - Errors when server in a foreach is unavailable
* [\#42](https://github.com/ironmansoftware/universal-dashboard/issues/42) - New-UDGrid/ServerSideProcessing
* [\#43](https://github.com/ironmansoftware/universal-dashboard/issues/43) - Out-UDGridData/DataTable
* [\#46](https://github.com/ironmansoftware/universal-dashboard/issues/46) - -DebugEndpoint is missing on New-UDTable in 1.5.1
* [\#47](https://github.com/ironmansoftware/universal-dashboard/issues/47) - DefaultRunspace is not set in the async task block that runs in the UDElement component 
* [\#52](https://github.com/ironmansoftware/universal-dashboard/issues/52) - UDMonitor - Index was out of range. Must be non-negative and less than the size of the collection. Parameter name: index
* [\#53](https://github.com/ironmansoftware/universal-dashboard/issues/53) - Error - Microsoft.Extensions.Logging.Filter.dll not being found since on OSX\Linux
* [\#78](https://github.com/ironmansoftware/universal-dashboard/issues/78) - Sync-UDElement







