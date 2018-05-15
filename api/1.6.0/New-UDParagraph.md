---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDParagraph

## SYNOPSIS
Creates a new paragraph block.

## SYNTAX

### content
```
New-UDParagraph [-Content <ScriptBlock>]
```

### text
```
New-UDParagraph [-Text <String>]
```

## DESCRIPTION
Creates a new paragraph block.

## EXAMPLES

### Example 1
```
PS C:\> New-UDParagraph -Content {
    "This is a paragraph of text"
}
```

Creates a new paragraph of text.

## PARAMETERS

### -Content
The content for this paragraph. 

```yaml
Type: ScriptBlock
Parameter Sets: content
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Text
Text for this paragraph.

```yaml
Type: String
Parameter Sets: text
Aliases: 

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

