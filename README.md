# Ansible Role: log2ram

![Test and release.](https://github.com/chzerv/ansible-role-log2ram/workflows/Test%20and%20release./badge.svg?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/ansible/role/50169?color=dodgerblue)](https://galaxy.ansible.com/chzerv/log2ram)

This role installs and configures [log2ram](https://github.com/azlux/log2ram) on Debian, Ubuntu, Archlinux, CentOS and Fedora systems. `log2ram` is mostly useful on systems which use an SD Card, like for example a Raspberry-Pi.

On Debian-based systems, the role uses the author's unofficial repository. On other distributions the installation is done manually.

## Requirements

None.

## Role Variables

Below is a list of the available variables and their default values. Make sure to also check the `defaults/main.yml` file.

```yaml
log2ram_enable_on_boot: true
```

> Whether to enable log2ram on boot or not.

```yaml
log2ram_reboot_after_install: true
```

> Whether to reboot the machine after instralling `log2ram` or not. The project's author recommends to reboot the machine after installing log2ram. **Note** that Ansible will wait for the systems to come back up and continue with the rest of the tasks.

```yaml
log2ram_state: install
```

> Possible values are:
>
> - `install` to install log2ram,
> - `remove` to uninstall log2ram and
> - `update` to update log2ram.

```yaml
log2ram_size: "40M"
```

> The ramdisk size. In case of the error `/var/log.hdd/ doesn't exist.Can't sync.`, the size has to be increased to a value > 40M!

```yaml
log2ram_use_rsync: "true"
```

> Whether to use `rsync` instead of `cp`. According to `log2ram`'s author, `rsync` offers better performance.

```yaml
log2ram_mail: "false"
```

> If set to `false`, the error system mail will be disabled if there's not enough space in RAM.

```yaml
log2ram_path_disk: "/var/log"
```

> Where the logs are saved.

```yaml
log2ram_use_zl2r: "false"
```

> Whether to enable `zram` compatibility. **Note** that zram **must** be already enabled and configured on the device if you want to use this.

```yaml
log2ram_compression_algorithm: "lz4"
```

> The compression algorithm used for zram. Check the project's [README](https://github.com/azlux/log2ram#install) for more information.

```yaml
log2ram_log_disk_size: "100M"
```

> The uncompressed zram size.


## Dependencies

None.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: server
  vars_files:
    - vars/main.yml

  roles:
    - { role: chzerv.log2ram }
```

The `vars/main.yml` file:

```yaml
---
log2ram_enable_on_boot: true
log2ram_reboot_after_install: true

log2ram_size: "50M"
log2ram_use_rsync: "false"
log2ram_mail: "true"
log2ram_path_disk: "/var/log"
log2ram_use_zl2r: "false"
log2ram_compression_algorithm: "lz4"
```

## License

MIT / BSD

## Author Information

Xristos Zervakis
