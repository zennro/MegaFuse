MegaFuse
========

This is a linux client for the MEGA cloud storage provider.
It is based on FUSE and it allows to mount the remote cloud drive on the local filesystem.
Once mounted, all linux program will see the cloud drive as a normal folder.

This software is based on FUSE.

The file are downloaded on the fly when requested and then cached to speedup processing.
The downloader will assign a higher priority to the requested chunk, and prefetch the remaining data.
This allows also fast streaming of video files without prior encoding.


please edit your config file "megafuse.conf" before running, you have to change at least your username and password.
The mountpoint must be an empty directory.
By default on debian system you need to be root to mount a fuse filesystem.
Optionally you can add this tool to /etc/fstab but this is untested,yet.

to run,just

	make
	./MegaFuse

to compile on debian 7 you need these additional packages:
	
	apt-get install libcrypto++ libcurl4-openssl-dev libdb5.1++-dev libfreeimage-dev 

you can pass additional options to the fuse module via the command line option -f. example:
	
	./MegaFuse -f -o allow_other -o uid=1000

after an abnormal termination you might need to clear the mountpoint:
	
	$ fusermount -u $MOUNTPOINT
	or # umount $MOUNTPOINT

I'm currently accepting donations via paypal at the address of my main project

	http://ygopro.it/web/modules.php?name=Donations&op=make
