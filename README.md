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
