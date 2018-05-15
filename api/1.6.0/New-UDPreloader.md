---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDPreloader

## SYNOPSIS
Creates a new preloader.

## SYNTAX

### indeterminate (Default)
```
New-UDPreloader [-BackgroundColor <DashboardColor>] [-ProgressColor <DashboardColor>]
```

### determinate
```
New-UDPreloader [-PercentComplete <Object>] [-BackgroundColor <DashboardColor>]
 [-ProgressColor <DashboardColor>]
```

### circular
```
New-UDPreloader [-Circular] [-Color <String>] [-Size <String>]
```

## DESCRIPTION
Creates a new preloader. Preloaders can be used to show progress or indicate to the user something is processing.

## EXAMPLES

### Example 1
```
PS C:\> New-UDPreloader -PercentComplete 10 
```

Creates a new determinate preloader with a percentage complete of 10.

## PARAMETERS

### -BackgroundColor
The background color of the preloader

```yaml
Type: DashboardColor
Parameter Sets: indeterminate, determinate
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Circular
Whether the preloadre is circular.

```yaml
Type: SwitchParameter
Parameter Sets: circular
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Color
The color of the preloader.

```yaml
Type: String
Parameter Sets: circular
Aliases: 
Accepted values: blue, red, green

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PercentComplete
The percent complete of the preloader.

```yaml
Type: Object
Parameter Sets: determinate
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProgressColor
The color of the preloaders progress.

```yaml
Type: DashboardColor
Parameter Sets: indeterminate, determinate
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Size
The size of the circular preloader.

```yaml
Type: String
Parameter Sets: circular
Aliases: 
Accepted values: small, medium, large

Required: False
Position: Named
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

