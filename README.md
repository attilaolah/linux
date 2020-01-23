# Linux Setup

> Contains a bunch of config files to make my Linux machines easily
> reproducible.

These days I run my Linux environments in some sort of containers. These are
mostly:

- [Crostini] on [ChromeOS]
- [Raspberry Pi] or other singleb-oard computers
- Cloud VMs

[Crostini]: https://chromium.googlesource.com/chromiumos/docs/+/master/containers_and_vms.md
[ChromeOS]: https://www.chromium.org/chromium-os
[Raspberry Pi]: https://www.raspberrypi.org

To make these more reproducible, I'm writing down some instructions here that
can be copy-pasted after a factory reset.

## Crostini Setup

Crostini runs a Linux container called `penguin` inside a VM called `termina`.
The default container is a Debian stable release, which I had some troubles
with in the past, particularly when trying to install multi-arch packages.

To fix that, I created an [Arch Linux] container by following
[these instructions](https://wiki.archlinux.org/index.php/Chrome_OS_devices/Crostini).
Detailed instructions on how to set up Arch can be found under [arch/].

[Arch Linux]: https://www.archlinux.org
[arch/]: arch/README.md

To destroy and re-create the VM and the container:

```sh
vmc destroy termina
vmc start termina
vmc container termina arch https://us.images.linuxcontainers.org archlinux/current
```
