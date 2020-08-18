# docker-sandbox
~~~~

~~~~

~~~~
$ sudo docker build -t ubuntu:helloworld-v2 . s/Dockerfile.helloworld.execform

[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v2
Hello docker
[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v2 betty
Hello betty
[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v2 john
Hello john

~~~~
~~~~
$ $ sudo docker build -t ubuntu:helloworld-v1 . --file=/vagrant/dockerfiles/Dockerfile.helloworld.shellform

[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v1 betty
Hello
[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v1 john
Hello
[vagrant@vg-docker-01 ~]$ sudo docker run -it ubuntu:helloworld-v1
Hello
~~~~

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

~~~~
$ hostnamectl
   Static hostname: vg-suricata-02
         Icon name: computer-vm
           Chassis: vm
        Machine ID: b82d4f866da945c7981fffdf2e981a94
           Boot ID: 04775c36d8b34766bc0fc76191746564
    Virtualization: oracle
  Operating System: Debian GNU/Linux 10 (buster)
            Kernel: Linux 4.19.0-6-amd64
      Architecture: x86-64

sudo docker build --rm -t local/c7-systemd . --file=/vagrant/dockerfiles/Dockerfile.centos.systemd
sudo docker build --rm -t local/c7-systemd-httpd . --file=/vagrant/dockerfiles/Dockerfile.apache
$ sudo docker run -ti -v /sys/fs/cgroup:/sys/fs/cgroup:ro -v /tmp/$(mktemp -d):/run -p 80:80 local/c7-systemd-httpd

curl http://localhost

This container is running with systemd in a limited context, with the cgroups filesystem mounted. There have been reports that if you're using an Ubuntu host, you will need to add -v /tmp/$(mktemp -d):/run in addition to the cgroups mount.
https://hub.docker.com/_/centos
~~~~
