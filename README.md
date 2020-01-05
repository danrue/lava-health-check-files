# LAVA Health Check Files

This repo uses git-lfs to persistently host some binary/build files for
perennial use in LAVA health checks. Namely, in
[lava-docker-compose](https://github.com/danrue/lava-docker-compose/) and
[lava.therub.org](https://github.com/danrue/lava.therub.org) repositories, as
well as anyone that is deriving work from them (which is encouraged).

To be doubly safe, reference the individual files using their specific commit
hash so that even if they are changed or removed in the future, your health
jobs will continue to work. Because it's so annoying when health check
artifacts disappear from the internet!

Example:

```yaml
actions:
- deploy:
    timeout:
      minutes: 3
    to: tmpfs
    os: oe
    images:
      kernel:
        image_arg: '-kernel {kernel} -append "console=ttyAMA0,115200 root=/dev/ram0 debug verbose"'
        url: https://github.com/danrue/lava-health-check-files/raw/854575d695fc7dd5261dd35e45e20f8b5e2ec5b1/health_checks/qemu/zImage
        sha256sum: ac04608b6fb548eb6eb97509e376aa4f7c7d74a22a4c14c4f1e6b46b2dcbfbd7
      ramdisk:
        image_arg: '-initrd {ramdisk}'
        url: https://github.com/danrue/lava-health-check-files/raw/854575d695fc7dd5261dd35e45e20f8b5e2ec5b1/health_checks/qemu/rootfs.cpio.gz
        sha256sum: 0a63d3a669cff57dca9eb5d45f476485ee46b9443ca2078feb860b7e90aeeb38
```
