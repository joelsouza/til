# Apple Silicon vs Docker Images

* Mac Apple silicon * processors use the ARM64 architecture instead of previous Intel's x86-64 generation.

Most of the Docker Official Images on Docker Hub provide a variety of architectures. For example, the `busybox` image supports `amd64`, `arm32v5`, `arm32v6`, `arm32v7`, `arm64v8`, `i386`, `ppc64le`, and `s390x`. When running this image on an `x86_64 / amd64` machine, the `amd64` variant is pulled and run.

Some images do not support the ARM64 architecture so we can add `--platform linux/amd64` to run (or build) an Intel image using emulation or:

```bash
  export DOCKER_DEFAULT_PLATFORM=linux/amd64
```

`Intel-based` containers on Apple silicon machines under emulation can crash as qemu sometimes fails to run the container. In addition, filesystem change notification APIs (inotify) do not work under qemu emulation. Even when the containers do run correctly under emulation, *they will be slower and use more memory than the native equivalent*.
