# Grids

Grids output data similar to tables but allow for paging and sorting the data in the grid. Grids are produced using the [Griddle ](https://griddlegriddle.github.io/Griddle/docs/)library. Grids are created with the New-UDGrid cmdlet and data for the grid is output using the Out-UDGridData cmdlet.

The below script selects the Name, Id, WorkingSet and CPU of ProcessInfo objects returned by Get-Process. The gird auto refreshes every minute.

```powershell
New-UdGrid -Title "Processes" -Headers @("Name", "ID", "Working Set", "CPU") -Properties @("Name", "Id", "WorkingSet", "CPU") -AutoRefresh -RefreshInterval 60 -Endpoint {
       Get-Process | Out-UDGridData
}
```

The above script produces the following grid.

![](/assets/griddle.png)

## Formatting DateTimes on the client 

If your data set includes a System.DateTime object as one of the properties, the UDGrid component will format the DateTime is the user's browsers local time zone settings. It uses [MomentJS](https://momentjs.com/docs/#/displaying/) to format the date time into a readable string. By default, it uses the `lll` format which yields a date time such as `Sep 4, 1986 8:30 PM`. You can customize the date time format by specifying the `-DateTimeFormat` on `New-UDGrid`. 

```powershell
New-UdGrid -Title "Files" -Headers @("Name", "Last Write Time") -Properties @("Name", "LastWriteTime") -AutoRefresh -RefreshInterval 60 -Endpoint {
       Get-ChildItem C:\temp |  | Out-UDGridData
} -DateTimeFormat 'LLLL'
```

## Including links in columns 

In addition to passing raw data down to a grid, you can also include links. Use the `New-UDLink` cmdlet to add links into columns. 

 ```powershell
$Data = @(
    [PSCustomObject]@{Animal="Frog";Order="Anura";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Frog")}
    [PSCustomObject]@{Animal="Tiger";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Tiger")}
    [PSCustomObject]@{Animal="Bat";Order="Chiroptera";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Bat")}
    [PSCustomObject]@{Animal="Fox";Order="Carnivora";Article=(New-UDLink -Text "Wikipedia" -Url "https://en.wikipedia.org/wiki/Fox")}
)

$Dashboard = New-UDDashboard -Title "Grids - Custom Columns" -Content {
    New-UDGrid -Title "Animals" -Headers @("Animal", "Order", "Wikipedia") -Properties @("Animal", "Order", "Article") -Endpoint {
        $Data | Out-UDGridData
    }
}
 ``` 