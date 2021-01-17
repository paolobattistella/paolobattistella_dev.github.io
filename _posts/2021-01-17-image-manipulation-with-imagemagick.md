---
layout: post
title: "Image manipulation with Image Magick"
categories: tools
---

## Convert from a format to another

convert img-from img-to

## Convert all the images in a folder from JPG to PNG

```
DESTFOLDER = './dest/'
cd .
for PHOTO in *.jpg
do
    FILENAME=${PHOTO%.jpg}
    convert "$PHOTO" "./$DESTFOLDER/$FILENAME.png"
    echo  "./$DESTFOLDER/FILENAME.png"
done
```

## Crop and scale

### Scale to a percentage of the original size

`convert -scale 50% img-from img-to`

### Scale to custom dimensions preserving aspect ratio

`convert -resize 600x600 screen.jpg`

e.g.

```
1920x1200 => 600x375
600x1200 => 300x600
150x300 => 300x600
300x150 => 600x300
```

`convert -resize 600x600\> screen.jpg`

e.g.

```
1920x1200 => 600x375
600x1200 => 300x600
150x300 => 150x300 (is not resized to bigger size)
300x150 => 300x150 (is not resized to bigger size)
```

### Scale to a percentage of the original size to create a thumbnail

`convert -thumbnail 50% img-from img-to`

### Create a thumbnail image with a given width (e.g. 170 pixels)

`convert -thumbnail 170x img-from img-to`

### Create a thumbnail image with a given height (e.g. 128 pixels)

`convert -thumbnail x128 img-from img-to

### Create a thumbnail image with a given height (e.g. 128 pixels)

`convert -thumbnail x128 img-from img-to`

## Set a filled background to image with transparent background layer

`convert -background white -alpha remove -alpha off img-from img-to`