# How to solve widevine and ffmpeg problems in Opera (Linux)

## Prerequisites
  - Google Chrome -  [here](https://www.google.pt/intl/pt-PT/chrome/)
  - Chromium-ffmpeg - [here](https://snapcraft.io/chromium-ffmpeg)
### Chromium-ffmpef (deb) version
  For those who prefer .deb versions, chromium is available for an unofficial [ppa](https://launchpad.net/~xalt7x/+archive/ubuntu/chromium-deb-vaapi)
  
## Widevine
  Opera's default configuration already pulls widevine files directly from Chrome, that is, their configuration is not necessary.
  
## FFmpeg
  In the snap version the files can be found like this:
```
   |-> / <- root directory
     |-> snap
       |-> chromium-ffmpeg
         |-> current
           |-> chromium-ffmpeg-*
             |-> chromium-ffmpeg
               |-> libffmpeg.so
```
#### Or
  For those who chose the (deb) version, the files can be found as follows:
```
  |-> usr
    |-> lib
      |-> chromium-browser
        |-> libffmpeg.so
```
## Configuring ffmpeg (Not needed for the (deb) version of chromium)
  The file to be modified is at:
```
  |-> usr
    |-> lib
      |-> x86_64-linux-gnu
        |-> opera
          |-> resources
            |-> ffmpeg_preload_config.json
```
  We will only inform the path of the libffmpeg.so files, it will change depending on the installed version of Chromium-ffmpeg as we have already seen.
  The original content of the files would be this:
```json
[
  "../../../../chromium-ffmpeg/libffmpeg.so",
  "/usr/lib/chromium-browser/libffmpeg.so",
  "/usr/lib/chromium-browser/libs/libffmpeg.so"
]
```
  After the added path it would look like this:
```json
[
  "../../../../chromium-ffmpeg/libffmpeg.so",
  "/usr/lib/chromium-browser/libffmpeg.so",
  "/usr/lib/chromium-browser/libs/libffmpeg.so",
  "/snap/chromium-ffmpeg/current/chromium-ffmpeg-95241/chromium-ffmpeg/libffmpeg.so"
]
```
  A list of versions of chromium-ffmpeg (snap):
  ```
    |-> / <- root directory
     |-> snap
       |-> chromium-ffmpeg
         |-> current
          |-> chromium-ffmpeg-91124
          |-> chromium-ffmpeg-91696
          |-> chromium-ffmpeg-92142
          |-> chromium-ffmpeg-92393
          |-> chromium-ffmpeg-92972
          |-> chromium-ffmpeg-93464
          |-> chromium-ffmpeg-94142
          |-> chromium-ffmpeg-95241
          |-> meta
          |-> snap
  ```
  All libffmpeg.so files found in the chromium-ffmpeg- * folders work, feel free to shrink anyone!
  
### Finishing
  After all this, save the edited files and restart your opera so that all modifications are effective
