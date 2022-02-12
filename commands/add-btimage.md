# Add-BTImage

### SYNOPSIS

Add an image to the body of a toaster notification.

### SYNTAX

```powershell
Add-BTImage -ContentBuilder <ToastContentBuilder> [[-Source] <String>] [-Crop <AdaptiveImageCrop>]
 [-AlternateText <String>] [-IgnoreCache] [-PassThru] [<CommonParameters>]
```

### DESCRIPTION

The Add-BTImage function adds an image to the body of a toast notification.

Multiple images can be added by calling the function multiple times. The images are displayed in the order in which they are added.

Any images added to the body of a toast notification are displayed after the text of the toast notification.

### EXAMPLES

#### EXAMPLE 1

```powershell
$Builder = New-BTContentBuilder
Add-BTImage -ContentBuilder $Builder -Source 'C:\Temp\LocalImage.png'
```

This example adds a local image to the body of a toast notification using a toast content builder object.

#### EXAMPLE 2

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source '\\\\FS01\Images$\NetworkImage.gif'
```

This example adds an image from a network share to the body of a toast notification with its toast content builder object coming from the pipeline.

#### EXAMPLE 3

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'https://example.com/OnlineImage.jpeg'
```

This example adds an image from the internet to the body of a toast notification.

Future invocations of this example will used a cached copy of the referenced image rather than going out to the internet again.

#### EXAMPLE 4

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'https://example.com/OnlineImage.jpeg' -IgnoreCache
```

This example adds an image from the internet to the body of a toast notification, it downloads the image from the internet regardless of if it has been previously cached.

#### EXAMPLE 5

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'C:\Temp\LocalImage.png' -AlternateText 'Picture of burnt toast, popped out of a toaster'
```

This example adds a local image to the body of a toast notification with supplied alt text to aid with accessibility e.g. the use of screen readers.

#### EXAMPLE 6

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'C:\Temp\LocalImage.png' -Crop Circle
```

This example adds a local image to the body of a toast notification cropped into the shape of a circle, overriding the default square shape.

#### EXAMPLE 7

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'C:\Temp\LocalImageOne.png'
$Builder | Add-BTImage -Source 'C:\Temp\LocalImageTwo.png'
```

This example adds two images to a toast content notification, which will be displayed in the order in which they are added.

#### EXAMPLE 8

```powershell
$Builder = New-BTContentBuilder
$Builder | Add-BTImage -Source 'C:\Temp\LocalImage.png' -PassThru |
           Add-BTText -Text 'First Line of Text' -PassThru |
           Add-BTText -Text 'Second Line of Text'
```

This example a image alongside three custom text elements to a toast content builder object on the pipeline by passing through a refference to the builder object.

The image is displayed after the text elements, despite being added first.

### PARAMETERS

#### -ContentBuilder

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

#### -Source

The URI of the image. Can be from your local computer, network location, or the internet. Online images will be downloaded and cached in the user's TEMP directory for future use.

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

#### -Crop

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

#### -AlternateText

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

#### -IgnoreCache

Specify that the online images should be downloaded, regardless of if they have been cached to the TEMP directory. Used when the online resource has been updated and you need to ensure that users see the latest version.

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

#### -PassThru

Returns an object that represents the item with which you're working. By default, this cmdlet doesn't generate any output.

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

#### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about\_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

### INPUTS

#### Microsoft.Toolkit.Uwp.Notifications.ToastContentBuilder

You can pipe a toast content builder object to Add-BTImage.

#### System.Uri

One image reference can be provided, this cannot be piped to Add-BTImage.

### OUTPUTS

#### None

The Add-BTImage function does not provide any output by default.

You can optionally use the PassThru parameter to output the updated toast content builder object, which enables chaining functions together.

### NOTES

You can reference an image from your local computer, a network location, or the internet.

Online images will be downloaded and cached in the user's TEMP directory for future use.

Animated GIFs and images with transparent background are supported.

### RELATED LINKS
