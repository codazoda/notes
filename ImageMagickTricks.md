# ImageMagick Tricks

A short list of Imagemagick command line tricks I find useful at times.

## Tile a Single Image

This command will tile the same image into a 2x2 pattern with no space between them.

`montage original.jpg original.jpg original.jpg original.jpg -geometry +0+0 -tile 2x2 new.jpg`

You can also flip/flop the images to make them more seemless.

`montage original.jpeg -flop original.jpeg -flip original.jpeg -flip original.jpeg -geometry +0+0 -tile 2x2 new.jpg`
