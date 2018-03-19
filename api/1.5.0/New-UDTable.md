---
external help file: PowerShellProTools.UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDTable

## SYNOPSIS
Creates a new table of data within the dashboard. 

## SYNTAX

```
New-UDTable [-Title <String>] -Headers <String[]> [-BackgroundColor <DashboardColor>]
 [-FontColor <DashboardColor>] [-Style <String>] [-DateTimeFormat <String>] [-Links <Link[]>]
 [-Endpoint <ScriptBlock>] [-AutoRefresh] [-RefreshInterval <Int32>] [-DebugEndpoint] [-Id <String>]
 [<CommonParameters>]
```

## DESCRIPTION
Creates a new table of data within the dashboard. 

## EXAMPLES

### Example 1
```
PS C:\>  New-UDTable -Title "Process Ids" -Header @("Name", "Process Id") -Endpoint {
    Get-Process -Name Chrome | Out-UDTableData -Property @("name", "id")
}
```

Creates a new table with the process IDs of chrome running on the system.

## PARAMETERS

### -AutoRefresh
Enabled auto refresh for this control.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BackgroundColor
Background color of the table.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DateTimeFormat
The date time format for date time columns.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DebugEndpoint
Runs the Endpoint in the UDDebug runspace.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Endpoint
The endpoint to call to retrieve data for the table. The endpoint should return data using the Out-UDTableData cmdlet.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FontColor
Font color within the table.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Headers
Headers for columns in the table. 

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of the table. This is the HTML markup ID.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Links
Links to display on the bottom of the table. Use New-UDLink to generate a link.

```yaml
Type: Link[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RefreshInterval
The number of seconds between refreshes. The default is 5.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Style
Allows for changing the style of the table.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 
Accepted values: bordered, striped, highlight, centered, responsive-table

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title
Title for the section containing the table.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

