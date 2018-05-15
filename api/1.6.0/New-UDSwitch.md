---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDSwitch

## SYNOPSIS
Creates a switch control. 

## SYNTAX

```
New-UDSwitch [[-Id] <String>] [[-OnText] <Object>] [[-OffText] <Object>] [-Disabled]
```

## DESCRIPTION
Creates a switch control. Switches are similar in function to checkboxes but use a different style.

## EXAMPLES

### Example 1
```
PS C:\> New-UDSwitch -OnText "yes" -OffText "No" 
```

Creates a switch that has yes and no as options.

## PARAMETERS

### -Disabled
Whether this switch is disabled.

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

### -Id
The ID of this switch.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OffText
The text displayed when this switch is in the off position.

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OnText
The text displayed when this switch is in the on position.

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
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

