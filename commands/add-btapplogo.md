# Add-BTAppLogo

## SYNOPSIS

Override the app logo with a custom image of choice that will be displayed on the toast.

## SYNTAX

```powershell
Add-BTAppLogo -ContentBuilder <ToastContentBuilder> [[-Source] <String>] [-Crop <AdaptiveImageCrop>]
 [-AlternateText <String>] [-IgnoreCache] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

The Add-BTAppLogo function specifies an image to be displayed on a toast notification as the app logo.

Prior to Windows 10 20H2 this app logo would replace the smaller icon that represents the source of a notification, but from 20H2 it is displayed in addition to the icon.

## EXAMPLES

### EXAMPLE 1

```powershell
$Builder = New-BTContentBuilder
```

PS C:\\\>Add-BTAppLogo -ContentBuilder $Builder -Source 'C:\Temp\LocalImage.png'

This example adds a local image as the app logo on the toast notification using a toast content builder object.

### EXAMPLE 2

```powershell
$Builder = New-BTContentBuilder
```

PS C:\\\>$Builder | Add-BTAppLogo -Source '\\\\FS01\Images$\NetworkImage.gif'

This example adds an image from a network share as the app logo on the toast notification being constructed.

### EXAMPLE 3

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTAppLogo -Source 'https://example.com/OnlineImage.jpeg'
```

This example adds an image from the internet as the app logo on the toast notification being constructed.

Future invocations of this example will used a cached copy of the referenced image rather than going out to the internet again.

### EXAMPLE 4

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTAppLogo -Source 'https://example.com/OnlineImage.jpeg' -IgnoreCache
```

This example adds an image from the internet as the app logo on the toast notification being constructed, it downloads the image from the internet regardless of if it has been previously cached.

### EXAMPLE 5

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTAppLogo -Source 'C:\Temp\LocalImage.png' -AlternateText 'Picture of burnt toast, popped out of a toaster'
```

This example adds a local image as the app logo on the toast notification with supplied alt text to aid with accessibility e.g.
the use of screen readers.

### EXAMPLE 6

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTAppLogo -Source 'C:\Temp\LocalImage.png' -Crop Circle
```

This example adds a local image as the app logo on the toast notification cropped into the shape of a circle, overriding the default square shape.

### EXAMPLE 7

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTAppLogo -Source 'C:\Temp\LocalImage.png' -PassThru |
           Add-BTText -Text 'First Line of Text' -PassThru |
           Add-BTText -Text 'Second Line of Text'
```

This example an app logo followed by three custom text elements to a toast content builder object on the pipeline by passing through a refference to the builder object.

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

### -Source

The URI of the image.
Can be from your local computer, network location, or the internet.
Online images will be downloaded and cached in the user's TEMP directory for future use.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $Script:DefaultImage
Accept pipeline input: False
Accept wildcard characters: False
```

### -Crop

Specify how the image should be cropped.

```yaml
Type: AdaptiveImageCrop
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Circle

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -AlternateText

A description of the image, for users of assistive technologies.

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

### -IgnoreCache

Specify that the online images should be downloaded, regardless of if they have been cached to the TEMP directory.
Used when the online resource has been updated and you need to ensure that users see the latest version.

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

You can pipe a toast content builder object to Add-BTAppLogo.

### System.Uri

One image reference can be provided, this cannot be piped to Add-BTAppLogo.

## OUTPUTS

### None

The Add-BTAppLogo function does not provide any output by default.

You can optionally use the PassThru parameter to output the updated toast content builder object, which enables chaining functions together.

## NOTES

You can reference an image from your local computer, a network location, or the internet.

Online images will be downloaded and cached in the user's TEMP directory for future use.

Animated GIFs and images with transparent background are supported.

## RELATED LINKS
