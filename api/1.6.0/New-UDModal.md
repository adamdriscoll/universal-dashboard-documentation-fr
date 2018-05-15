---
external help file: UniversalDashboard-help.xml
online version: 
schema: 2.0.0
---

# New-UDModal

## SYNOPSIS
Creates a modal.

## SYNTAX

```
New-UDModal [[-Id] <String>] [[-Header] <String>] [[-Content] <ScriptBlock>]
```

## DESCRIPTION
Creates a modal.

## EXAMPLES

### Example 1
```
PS C:\> New-UDModal -Header "My modal" -Content {
    New-UDCard -Title "My Content"
}
```

Creates a modal with the header My modal and a card as the content.

## PARAMETERS

### -Content
The content of the modal.

```yaml
Type: ScriptBlock
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header
The header for the modal.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id
The ID of the modal.

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

