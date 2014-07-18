# GifFrameExtractor

GifFrameExtractor is a PHP class that separates all the frames (and their durations) of an animated GIF.

### For what ?

The class helps you separate all the frames of an animated GIF, for example to watermark them and then to
generate a new watermarked and animated GIF.

### Usage

GifFrameExtractor is really easy to use:

**1 - Extraction:**

```php
$gifFilePath = 'path/images/picture.gif';

if (GifFrameExtractor::isAnimatedGif($gifFilePath)) { // check that this is an animated GIF
    
    $gfe = new GifFrameExtractor();
    $gfe->extract($gifFilePath);
    
    // Do something with the extracted frames ...
}
```

**2 - Getting the frames and their durations:**

```php
foreach ($gfe->getFrames() as $frame) {
    
    // The frame resource image var
    $img = $frame['image'];
    
    // The frame duration
    $duration = $frame['duration'];
}
```

You can also get a separate array of images and durations:

```php
$frameImages = $gfe->getFrameImages();
$frameDurations = $gfe->getFrameDurations();
```

You can also obtain the following information:

```php
$totalDuration = $gfe->getTotalDuration(); // Total duration of the animated GIF
$frameNumber = $gfe->getFrameNumber(); // Number of extracted frames
var_dump($gfe->getFrameDimensions()); // An array containing the dimension of each extracted frame
var_dump($gfe->getFramePositions()); // An array containing the original positions of each extracted frame inside the GIF
```

**Option:**

You can choose if you want to get the original frames (with transparency background) or frames pasted on the first one
with the second parameter of extract() method:

```php
$gfe->extract('path/images/picture.gif', true); // Can get transparent orignal frames
```

This option is false by default.

### About

The class reuses some part of code of "PHP GIF Animation Resizer" by Taha PAKSU (thanks to him).
