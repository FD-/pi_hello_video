# Raspberry Pi hello video
Fork of hello_video example from Raspberry Pi sample code that provides seamless looping of a raw H264 video stream.  Original code is available at: https://github.com/raspberrypi/userland/tree/master/host_applications/linux/apps/hello_pi

This repository was modified yet again in order to demonstrate issues with flushing the video pipeline:

Compiling the code as-is demonstrates that despite flushing the pipeline after all data is fed into it, the last frame is still stuck at the end.
Adding another getchar() above the flush, you can see that suddenly, the flush seems to clear the last frame. This indicates the problem is linked to timing.
When uncommenting the workaround, you can see that sending an empty buffer through the pipeline seems to also 'fix' the issue.

Build by executing `rebuild.sh`.

Run by executing `hello_video.bin test.h264`. By default, the video will loop infinitely.
