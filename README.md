# Add ffmpeg with aac support to Docker Homebridge (Alpine version)

Solves the error of missing libfdk_aac. Folders were copied from https://hub.docker.com/r/alfg/ffmpeg, inspired by https://github.com/nicholasrobinson/ffmpeg-homebridge/blob/master/Dockerfile.

Add this to the container startup script:

```bash
apk del ffmpeg ffmpeg-libs
wget https://github.com/mfoll/ffmpeg_aac/raw/master/opt_ffmpeg.zip
unzip opt_ffmpeg.zip
mv opt_ffmpeg/ /opt/ffmpeg
rm opt_ffmpeg.zip
wget https://github.com/mfoll/ffmpeg_aac/raw/master/usr_lib.zip
unzip usr_lib.zip
mv usr_lib/* /usr/lib/
rm -r usr_lib/
rm usr_lib.zip
rm /usr/bin/ffmpeg
rm /usr/bin/ffprobe
ln -s /opt/ffmpeg/bin/ffmpeg /usr/bin/ffmpeg 
ln -s /opt/ffmpeg/bin/ffprobe /usr/bin/ffprobe 
```
