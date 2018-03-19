---
external help file: UniversalDashboard-help.xml
Module Name: UniversalDashboard
online version: 
schema: 2.0.0
---

# Remove-UDCookie

## SYNOPSIS
Removes an HTTP cookie

## SYNTAX

```
Remove-UDCookie [-Name] <String> [[-CookieOptions] <CookieOptions>] [<CommonParameters>]
```

## DESCRIPTION
Removes an HTTP cookie. This cmdlet is intended to be called in an Endpoint.

## EXAMPLES

### Example 1
```
PS C:\> New-UDInput -SubmitText "Remove Cookie" -Endpoint {
                param() 

                Remove-UDCookie -Name "Hello"

                New-UDInputAction -Toast "Cookie removed"
            }
```

Removes the cookie "Hello" when the user clicks the Remove Cookie button. 

## PARAMETERS

### -CookieOptions
HTTP cookie options for the cookie to remove.

```yaml
Type: CookieOptions
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
The name of the cookie to remove.

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

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

