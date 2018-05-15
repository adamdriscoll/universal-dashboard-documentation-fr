---
external help file: PowerShellProTools.UniversalDashboard.dll-Help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# New-UDRow

## SYNOPSIS
Creates a new row on the dashboard.

## SYNTAX

```
New-UDRow [[-Columns] <ScriptBlock>] [-Endpoint <ScriptBlock>] [-AutoRefresh] [-RefreshInterval <Int32>]
 [-DebugEndpoint] [-Id <String>] [<CommonParameters>]
```

## DESCRIPTION
Creates a new row on the dashboard. Columns are defined with New-UDColumn.

## EXAMPLES

### Example 1
```
PS C:\> New-UDRow {
	New-UDColumn -Size 6 {
	
	}
	New-UDColumn -Size 6 {
	
	}
}
```

Defines a row with two columns are equal size.

### Example 2
```
PS C:\> New-UDRow {
	New-UDColumn -Size 6 {
		New-UDRow {
			New-UDColumn -Size 6 {
			
			}
			New-UDColumn -Size 6 {
			
			}
		}
	}
	New-UDColumn -Size 6 {
	
	}
}
```

Defines a row with two columns are equal size. Inside the first column is another row with two columns.

## PARAMETERS

### -AutoRefresh
Whether this row should autorefresh. 

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

### -Columns
The columns to define for the row. These columns should be defined using New-UDColumn.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
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
The endpoint to call when generating the content for this row. 

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

### -Id
The ID of the row. This is the HTML markup ID.

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

### -RefreshInterval
The number of seconds between refreshes. 

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

