---
Created:  '2021-08-17 08:28:25 +01:00'
Modified: '2021-08-17 08:28:25 +01:00'
---


| Tags: #tools #ctf #pentesting #infosec #kali |
| -------------------------------------------- |

---
# ExifTool

Displays exif info on the command line. 

CTFs commonly hide data in the EXIF part of images and/or audio files.



-   If you have an image where the data you need is covered, try viewing the thumbnail:

```
exiftool -b -ThumbnailImage my_image.jpg > my_thumbnail.jpg
```