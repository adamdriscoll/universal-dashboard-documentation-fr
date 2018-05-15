---
external help file: PowerShellProTools.UniversalDashboard.dll-Help.xml
online version: 
schema: 2.0.0
---

# Send-UDToast

## SYNOPSIS
Sends a toast message from an endpoint.

## SYNTAX

```
Send-UDToast [-Message] <String> [-Duration <Int32>]
```

## DESCRIPTION
Sends a toast message from an endpoint.

## EXAMPLES

### Example 1
```
PS C:\> New-UDButton -Text "Click me" -OnClick {
    Send-UDToast -Message 'Ouch!"
}
```

Sends a toast to the user when the button is clicked. 

## PARAMETERS

### -Duration
The number of seconds to show the toast.

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

### -Message
A message to show to the user. 

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

