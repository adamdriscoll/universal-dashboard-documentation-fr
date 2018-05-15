---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDHeading

## SYNOPSIS
Creates a heading.

## SYNTAX

```
New-UDHeading [[-Id] <String>] [[-Content] <Object>] [[-Size] <Object>] [[-Color] <DashboardColor>]
```

## DESCRIPTION
Creates a heading.

## EXAMPLES

### Example 1
```
PS C:\> New-UDHeading -Size 3 -Content { "Header" }
```

Creates the heading "Header" with a size of 3. 

## PARAMETERS

### -Color
Font color for the heading.

```yaml
Type: DashboardColor
Parameter Sets: (All)
Aliases: 

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Content
Content for the heading.

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

### -Id
The ID of this heading.

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

### -Size
Size of this heading from 1 to 6. 1 is the largest and 6 is the smallest.

```yaml
Type: Object
Parameter Sets: (All)
Aliases: 
Accepted values: 1, 2, 3, 4, 5, 6

Required: False
Position: 2
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

