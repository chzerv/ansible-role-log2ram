# Ansible Role: log2ram

This role installs and configures [log2ram](https://github.com/azlux/log2ram) on Debian, Ubuntu, Archlinux, CentOS and Fedora systems. `log2ram` is mostly useful on systems which use an SD Card, like for example a Raspberry-Pi.

On Debian-based systems, the role uses the author's unofficial repository. On other distributions the installation is done manually.

## Requirements

None.

## Role Variables

```yaml
log2ram_enable_on_boot: true
```

> Whether to enable log2ram on boot or not.

```yaml
log2ram_reboot_after_install: false
```

> The project's author recommends to reboot the machine after installing log2ram. **Note** that Ansible will wait for the systems to come back up and continue with the rest of the tasks.

```yaml
log2ram_size: "40M"
```

> The ramdisk size. In case of the error `/var/log.hdd/ doesn't exist.Can't sync.`, the size has to be increased to a value > 40M!

```yaml
log2ram_use_rsync: "false"
```

> Whether to use `rsync` instead of `cp`.

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
```

## License

MIT / BSD

## Author Information

Xristos Zervakis
