Docker Tips
-----------

Overview and configuration details are given in [Docker](docker.md).

### Start/Detach/Stop/Restart

    docker run --name CONT -it debian bash -l   # No `--rm` option
    #   ^P^Q to detach.
    docker attach CONT          #   End existing process with ^D
    docker start -a CONT        #   End new process with ^D
    docker rm CONT

### Separate Shell Process in Running Docker Container

    docker exec -it CONTAINER bash -l

* `-i`: Interactive, keep STDIN open even if not attached
* `-t`: Allocate a pseudo-TTY

### Usage of Docker Volumes

    docker volume create VOL
    docker run -it --rm --mount=type=volume,destination=/mnt,source=MYVOL ubuntu
    docker volume rm VOL

### Leveraging Docker for Root Access

On most systems there is a `docker` group with access to the Docker
daemon socket. Anybody in this group should also be explictly allowed
to sudo to a root shell. If they can't, they can leverage their
implict access via:

    #   On the host, start a Docker container with a root shell
    #   that has access to all files on the host.
    docker run -it --rm --name root -v /:/host:rw alpine /bin/bash -l

    #   You are now running as root user in the docker container.
    #   Allow user `taro` to sudo to a root shell with no password.
    cd /host/etc/sudoers.d
    echo 'taro ALL=(ALL) NOPASSWD:ALL' > 50-taro
    chmod 600 50-taro
    exit

### Checking If You're Running in a Container

[This SO answer][so-23513045] suggests checking `/proc/1/cgroup` to
see if you're at the root for all hierarchies (e.g., `3:cpuset:/`).
However, as per my comment there, newer systemd versions (e.g.,
Debian 9 systemd 232) may have many cgroups set to `/init.scope`.
The most reliable heurstic I can think of at the moment is:

    grep -s -q ':/docker/' /proc/1/cgroup



[so-23513045]: https://stackoverflow.com/q/23513045/107294