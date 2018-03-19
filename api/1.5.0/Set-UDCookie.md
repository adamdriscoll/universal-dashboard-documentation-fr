---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# Set-UDCookie

## SYNOPSIS
Sets an HTTP cookie to a specified value.

## SYNTAX

```
Set-UDCookie [-Name] <String> [-Value] <String> [[-CookieOptions] <CookieOptions>] [<CommonParameters>]
```

## DESCRIPTION
Sets an HTTP cookie to a specified value. This cmdlet is intended to be called from an endpoint.

## EXAMPLES

### Example 1
```
PS C:\> New-UDInput -Id "Input" -Title "Input Cookie" -Endpoint {
                param([string]$Name, [string]$Value)

                Set-UDCookie -Name $Name -Value $Value
            }
```

Sets a cookie to the HTTP session based on the name and value specified by the user. 

## PARAMETERS

### -CookieOptions
Cookie options for the cookie.

```yaml
Type: CookieOptions
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of the cookie.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value
The value of the cookie.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: True
Position: 1
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

