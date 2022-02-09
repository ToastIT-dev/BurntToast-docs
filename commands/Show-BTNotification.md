# Show-BTNotification

## SYNOPSIS

Shows a new toast notification.

## SYNTAX

```powershell
Show-BTNotification [-ContentBuilder] <ToastContentBuilder[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

The Show-BTNotification function shows a new toast notification with its configured content.

## EXAMPLES

### EXAMPLE 1

```powershell
Show-BTNotification -ContentBuilder $ToastContentBuilder
```

This command displays a toast notification with the content of the ToastContentBuilder object.

### EXAMPLE 2

```powershell
$ToastContentBuilder | Show-BTNotification
```

This command displays a toast notification with the content of the ToastContentBuilder object supplied via the pipeline.

### EXAMPLE 3

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text', 'Second Line of Text'
Show-BTNotification -ContentBuilder $Builder
```

This example demonstrates the full life cycle of a ToastContentBuilder object from creation to display.

## PARAMETERS

### -ContentBuilder

{{ Fill ContentBuilder Description }}

```yaml
Type: ToastContentBuilder[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

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

### Microsoft.Toolkit.Uwp.Notifications.ToastContentBuilder

You can pipe a toast content builder object to Show-BTNotification.

## OUTPUTS

### None

## NOTES

## RELATED LINKS
