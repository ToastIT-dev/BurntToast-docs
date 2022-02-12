# Add-BTText

## SYNOPSIS

Add text to the toast.

## SYNTAX

### CustomText (Default)

```powershell
Add-BTText -ContentBuilder <ToastContentBuilder> [-Text] <String[]> [-MaxLines <Int32>] [-Language <String>]
 [-PassThru] [<CommonParameters>]
```

### AttributionText

```powershell
Add-BTText -ContentBuilder <ToastContentBuilder> [-Text] <String[]> [-MaxLines <Int32>] [-Attribution]
 [-Language <String>] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

The Add-BTText function adds custom text to a toast notification via a content builder object.

By default this text will be added to the body of the toast. You can also add attribution text using the Attribution switch.

## EXAMPLES

### EXAMPLE 1

```powershell
$Builder = New-BTContentBuilder
Add-BTText -ContentBuilder $Builder -Text 'First Line of Text'
```

This example adds one custom text element to the toast content builder object stored in the $Builder variable using the ContentBuilder parameter explicitly.

### EXAMPLE 2

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text'
```

This example adds one custom text element to the toast content builder object stored in the $Builder variable by piping it into the Add-BTText function.

### EXAMPLE 3

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text', 'Second Line of Text'
```

This example adds two custom text elements to a toast content builder object with a single call of the Add-BTText function.

### EXAMPLE 4

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text'
$Builder | Add-BTText -Text 'Second Line of Text'
```

This example adds two custom text elements to a toast content builder object with two discrete calls of the Add-BTText function.

### EXAMPLE 5

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text' -PassThru |
           Add-BTText -Text 'Second Line of Text' -PassThru |
           Add-BTText -Text 'Third Line of Text'
```

This example adds three custom text elements to a toast content builder object using multiple calls of the Add-BTText function on the pipeline.

The PassThru parameter is used to pass the toast content builder down the pipeline.
Note that this is not required at the end of the pipeline as the builder object being added to is already stored in a variable.

### EXAMPLE 6

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text'
$Builder | Add-BTText -Text 'Second Line of Text'
$Builder | Add-BTText -Text 'Third Line of Text'
$Builder | Add-BTText -Text 'Fourth Line of Text'
```

This example attempts to add four custom text elements to a toast content builder object.

Only the first three of these elements will be added and the fourth will generate a warning stating that the maximum number of lines has been reached.

### EXAMPLE 7

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text' -MaxLines 1
$Builder | Add-BTText -Text 'Second Line of Text',
                            'Third Line of Text',
                            'Fourth Line of Text'
```

This example sets the max lines for the first custom text element to 1, overriding the default value of 2.

This means the toast notification can now accept four custom text elements, each with a max line count of 1, for a total line count of 4.

### EXAMPLE 8

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'First Line of Text' -Language en-NZ
```

This example specifies that the language included in the text element is New Zealand English using the relevant BCP-47 code, en-NZ.

### EXAMPLE 9

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTText -Text 'Example Toast Source' -Attribution
```

This example add attribution test to a toast notification.

## PARAMETERS

### -ContentBuilder

The toast content builder object that represents the toast notification being constructed.

```yaml
Type: ToastContentBuilder
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Text

Custom text to display on the tile.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxLines

The maximum number of lines the text element is allowed to display.

```yaml
Type: Int32
Parameter Sets: CustomText
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Attribution

Specifies that the text should be added as attribution text.

```yaml
Type: SwitchParameter
Parameter Sets: AttributionText
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Language

The target locale of the toast notification, specified as a BCP-47 language tags such as "en-US" or "fr-FR".
The locale specified here overrides any other specified locale, such as that in binding or visual.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Returns an object that represents the item with which you're working.
By default, this cmdlet doesn't generate any output.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Toolkit.Uwp.Notifications.ToastContentBuilder

You can pipe a toast content builder object to Add-BTText.

### System.String

You can provide multiple strings at once, but they cannot be piped.

## OUTPUTS

### None

The Add-BTText function does not provide any output by default.

You can optionally use the PassThru parameter to output the updated toast content builder object, which enables chaining functions together.

## NOTES

A toast notification can contain a maximum of four reserved lines of text.
By default this means you can include three customer text elements as the first, which acts like a heading, automatically reserves 2 lines.

You can override this behavior using the MaxLines parameter, specifically by setting the first line to a maximum of 1 line.

This function will ignore any text elements that would exceed this limit and output a warning stating this.

Attribution text is displayed underneath other text elements, but above image elements.
You can only have one attribution text element per toast notification and adding attribution to a notification will override any existing attribution text.

## RELATED LINKS
