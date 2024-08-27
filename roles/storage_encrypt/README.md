# Encrypt Disk Role

## Description

This role is designed to encrypt a secondary disk on a system using LUKS. It performs the following tasks:

1. **Install necessary packages**: Installs `cryptsetup` required for disk encryption.
2. **Partition checks**: Gathers disk facts, checks if partitions are not the root partition, and determines if the partition is already encrypted.
3. **Encryption**: Encrypts the partition if it is not already encrypted and opens it.
4. **Filesystem setup**: Formats the opened LUKS partition as `ext4`.
5. **Mounting**: Creates a mount point directory, mounts the encrypted partition, and persists the mount in `/etc/fstab`.

## Variables
In the `group_vars/servers.yml` specify partition name and in the `./defaults/main.yml`, specify passphrase to encrypt partition. Also you can add to `host_vars` yaml file with name as your hostname and add partition name there to define partition name for specific host.

- `luks_passphrase`: The passphrase for LUKS encryption.
- `luks_name`: The name for the LUKS container.
- `mount_point`: The directory where the encrypted partition will be mounted.

## Supported Platforms
- Ubuntu (22.04, 24.04)
