---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDSpan

## SYNOPSIS
Creates a span of content.

## SYNTAX

```
New-UDSpan [[-Id] <String>] [[-Content] <Object>]
```

## DESCRIPTION
Creates a span of content.

## EXAMPLES

### Example 1
```
PS C:\> New-UDSpan -Content {
    New-UDHeading -Text "Header"
}
```

Creates a header within a span. 

## PARAMETERS

### -Content
Content for this span.

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
The ID for this span.

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

## INPUTS

### None


## OUTPUTS

### System.Object

## NOTES

## RELATED LINKS

