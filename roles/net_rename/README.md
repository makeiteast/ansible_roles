# Rename Network Interface Role

This role configures the server's network interface using Netplan. It ensures the appropriate Netplan configuration file is backed up, modified, and applied. 

## Variables
In the `./defaults/main.yml`, specify new network interface name.

- `new_interface_name`: The new name for the network interface (default: `net0`)
- `attr_name`: The attribute to set for the interface (default: `set-name`)
- `interface_name`: The current interface name.
- `mac`: The MAC address of the interface.
## Supported Platforms
- Ubuntu (22.04, 24.04)


### Tasks

1. Check for the presence of Netplan configuration files.
2. Back up the existing Netplan configuration.
3. Parse and update the Netplan configuration to rename the interface.
4. Apply the Netplan configuration changes.
5. Restore the original Netplan configuration if the application of the changes fails.

### Handlers

This role contains handlers to apply Netplan changes after modifications to the configuration files.