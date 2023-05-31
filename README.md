Ansible Role: Mount
=========

An Ansible role for managing mount points.

Requirements
------------
This Ansible role has been developed and thoroughly tested with Ansible Core version 2.15.0.

This role was designed for:

- CentOS 8 Stream
- RHEL 8

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

[ansible-galaxy-requirements.yml](ansible-galaxy-requirements.yml)

You can install these collections using the following commands:

```shell
ansible-galaxy role install -r ansible-galaxy-requirements.yml
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
