# Manage Intel Idle Driver Role

This role manages Intel Idle Driver settings by modifying GRUB configuration and rebooting the system.

## Requirements

- Ensure the system has Ansible installed.
- Supported platforms: Ubuntu 22.04, 24.04.

## Role Variables

- `grub_file_path`: Path to the GRUB configuration file.
- `intel_idle_cstate`: Max C-state setting for the Intel Idle Driver.

## Supported Platforms
- Ubuntu (22.04, 24.04)
