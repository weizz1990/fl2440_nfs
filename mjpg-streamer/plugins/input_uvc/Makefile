###############################################################
#
# Purpose: Makefile for "M-JPEG Streamer"
# Author.: Tom Stoeveken (TST)
# Version: 0.3
# License: GPL
#
###############################################################

CC = gcc

OTHER_HEADERS = ../../mjpg_streamer.h ../../utils.h ../output.h ../input.h

CFLAGS += -O2 -DLINUX -D_GNU_SOURCE -Wall -shared -fPIC -I/home/huniu/sources/mjpeg_streamer/jpeg-6b-build/include
#CFLAGS += -DDEBUG
LFLAGS += -lpthread -ldl

all: input_uvc.so

clean:
	rm -f *.a *.o core *~ *.so *.lo

input_uvc.so: $(OTHER_HEADERS) input_uvc.c v4l2uvc.lo jpeg_utils.lo dynctrl.lo
	$(CC) $(CFLAGS) -ljpeg -L/home/huniu/sources/mjpeg_streamer/jpeg-6b-build/lib -o $@ input_uvc.c v4l2uvc.lo jpeg_utils.lo dynctrl.lo

v4l2uvc.lo: huffman.h uvc_compat.h uvcvideo.h v4l2uvc.c v4l2uvc.h
	$(CC) -c $(CFLAGS) -o $@ v4l2uvc.c

jpeg_utils.lo: jpeg_utils.c jpeg_utils.h
	$(CC) -c $(CFLAGS) -o $@ jpeg_utils.c

dynctrl.lo: dynctrl.c dynctrl.h uvcvideo.h
	$(CC) -c $(CFLAGS) -o $@ dynctrl.c
