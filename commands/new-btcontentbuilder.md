# New-BTContentBuilder

## SYNOPSIS

Create a toast builder object.

## SYNTAX

```powershell
New-BTContentBuilder [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

The New-BTContentBuilder function creates a new toast content builder object to construct a complete notification.

## EXAMPLES

### EXAMPLE 1

```powershell
$Builder = New-BTContentBuilder
```

This example creates a new toast content builder object and storing it in a variable named $Builder.

### EXAMPLE 2

```powershell
$Builder = Builder
```

This example creates a new toast content builder object using the Builder alias and storing it in a variable named $Builder.

## PARAMETERS

### -WhatIf

Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

You cannot pipe objects to New-BTContentBuilder.

## OUTPUTS

### Microsoft.Toolkit.Uwp.Notifications.ToastContentBuilder

## NOTES

## RELATED LINKS
