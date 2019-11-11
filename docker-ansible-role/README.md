# docker-sandbox
~~~~
vagrant up

$ sudo docker build -t test . --file=/vagrant/dockerfiles/debian-base

$ sudo docker run -it test
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.067 ms

$ docker run -it test google.com
PING google.com (172.217.169.110) 56(84) bytes of data.
64 bytes from sof02s31-in-f14.1e100.net (172.217.169.110): icmp_req=1 ttl=54 time=22.1 ms
~~~~
~~~~
$ sudo docker build -t testv1 . --file=/vagrant/dockerfiles/debian-basev1

$ sudo docker run -it testv1
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.067 ms

$ sudo docker run -it testv1 bash
root@fc91bcc07f4f:/#
~~~~
overide entrypoint
~~~~
$ docker run -it --entrypoint="/bin/bash" testv1
root@039adbbef014:/# exit
..
~~~~
no entrypoint
~~~~
$ docker run testv1 /bin/cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
~~~~
with entry point
~~~~
$ docker run --entrypoint="/bin/cat" testv1 /etc/passwd
root:x:0:0:root:/root:/bin/bash
...
~~~~
~~~~
$ sudo docker build -t testv2 . --file=/vagrant/dockerfiles/debian-basev2
$ docker run testv2 /etc/passwd
root:x:0:0:root:/root:/bin/bash
~~~~
~~~~
<-- /bin/bash overrides CMD
<-- /bin/bash does not override ENTRYPOINT
docker run -it --rm testv2  /bin/bash

<-- overrides ENTRYPOINT with ls
$ docker run -it --rm --entrypoint ls testv2  /bin/bash
/bin/bash

<-- overrides ENTRYPOINT with ls and overrides CMD with -la
$ docker run -it --rm --entrypoint ls testv2  /bin/bash -la
-rwxr-xr-x. 1 root root 975488 Oct 26  2016 /bin/bash

~~~~
~~~~
$ sudo docker build -t custom_sleep . --file=/vagrant/dockerfiles/debian-basev3
$ docker run custom_sleep

override the command
$ docker run custom_sleep sleep 15

$ sudo docker build -t custom_sleep . --file=/vagrant/dockerfiles/debian-basev4
~~~~
