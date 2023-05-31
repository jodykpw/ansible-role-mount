Ansible Role: Mount
=========

An Ansible role for managing mount points.

Requirements
------------

The target host should be running a compatible operating system and have the `mount` command available.

Role Variables
--------------

The `mode`, `owner` and `group` can be set in the `mount_points` list, but
when not specified, these defaults are used.

    mount_default_mode: "700"
    mount_default_owner: root
    mount_default_group: root

All parameters can be found in the following link:
https://docs.ansible.com/ansible/latest/collections/ansible/posix/mount_module.html#parameters

Example Mount an NFS volume

    mount_points:
      - path: /data/nas/provisioner/hdd
        src: 192.168.1.1:/provisioner
        opts: intr,noatime,vers=4.1,rsize=32768,wsize=32768
        fstype: nfs
        state: mounted

Example absent_from_fstab specifies that the device mount’s entry will be removed from fstab. This option does not unmount it or delete the mountpoint.

    mount_points:
      - path: /data/nas/provisioner/hdd
        src: 192.168.1.1:/provisioner
        opts: intr,noatime,vers=4.1,rsize=32768,wsize=32768
        fstype: nfs
        state: absent_from_fstab

Dependencies
------------

This role depends on the following Ansible Galaxy collections:

- `community.general`: Provides a wide range of additional modules and plugins for Ansible.
- `ansible.posix`: Offers modules specifically designed for POSIX-compliant systems, including the `mount` module.

You can install these collections using the following commands:

```shell
ansible-galaxy collection install community.general
ansible-galaxy collection install ansible.posix
```

Example Playbook
----------------

    - hosts: all
      become: true
      vars_files:
        - group_vars/mounts.yml
      roles:
        - ansible-role-mount

License
-------

MIT / BSD

🇬🇧🇭🇰 Author Information
------------------

* Author: Jody WAN
* Linkedin: https://www.linkedin.com/in/jodywan/
* Website: https://www.jodywan.com
