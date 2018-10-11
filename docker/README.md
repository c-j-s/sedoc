Docker
======

Documentation:
* [Docker Image Creation and Maintenance](image.md)
* [Docker Installation and Configuration](config.md)
* [Docker Security](security.md)
* [Docker Tips](tips.md) for handy commands and the like.
* [Reference documentation] for complete documentation.
* [Engine CLI] for `docker` command details.
  (This provides a lot of information not in the manpages.)


Terminology
-----------

A Docker __container__ is one or more process with their own
configuration for access to disk/network resources, UIDs/GIDs, etc. on
the host. Each container has its own disk store for the root volume
and may also have host resources mounted in it. The initial disk store
for a container is created from an __image__.

Each Docker instance has a local set of images; these are either
created locally using the [docker build] process or pulled (copied)
from a registry. Images are identified by a unique __image id__; this is
generated at the time it's built and will be different for another
build from the same image description. Images may also be identified
by a __tag__ local to the image store (e.g. `alpine:latest`); the tag
within a store may point to different images over time.

Images include a list of references to __layers__ containing the
changed files that [contribute to a derived container's
filesystem][image-ids]. The layers are identified by a __digest__ of
the tarball containing the files changed in that layer in the form
_algo:hexstring_, e.g., `sha256:fc92ee...`. There is also a separate
digest for the compressed version of the layer used in registry
manifests. Layers have no notion of an image or of belonging to an
image, they are merely collections of files and directories.

A __registry__ is an image store from which one can __pull__ images to
or __push__ images from a local Docker instance. Registries use a
standard [HTTP API] currently at version 2. Images in registries are
stored in collections known as __repositories__; each collection
usually contains different versions of an image designed for a
particular purpose (e.g., `alpine`). See the [Docker Hub] registry
(and below) for an example.

[image-ids]: https://windsock.io/explaining-docker-image-ids/


Further Reading
-------------

* [Terra Nullius](https://alexei-led.github.io/).
  Blog that covers "everday hacks for docker," e.g. [multi-stage
  build](https://alexei-led.github.io/post/node_docker_multistage/).