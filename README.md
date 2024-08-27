## README

### Overview

This repository contains an Ansible role and playbook designed to prepare an Ubuntu server for operation. The role focuses on system configuration tasks such as disk encryption, CPU settings adjustments, and network interface renaming, ensuring repeatability across multiple servers. The primary goal is to automate OS preparation tasks for easier server configuration and management.

### Features

The Ansible role performs the following tasks:

1. **Disk Encryption**:
   - Encrypt the second disk in the system (specified in the inventory and not containing the root partition).
   - Encrypt the partition that resides next to the root partition on the primary disk.

2. **CPU Configuration**:
   - Disable C-state for all available CPUs.
   - Switch CPU operation mode from power-saving to performance mode.

3. **Network Interface Management**:
   - Rename the active network interface to `net0`.
   - Display information about the renamed interface after the playbook execution.

4. **System Information Display**:
   - At the end of the playbook execution, display a list of CPUs and information about Intel Hyper-Threading or AMD multithreading.

### Prerequisites

- **Ansible**: Ensure that Ansible is installed on your control node.
- **Ubuntu Server**: The target server should be running Ubuntu 22.04 or 24.04 as the base OS.

### Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Define the Inventory**:
   - In the `inventories/hosts`, specify the target hosts.
   - Example:
     ```
        [servers]
        server1 ansible_host=xxx.xxx.xxx.xxx ansible_user=host_username
     ```
    - In the `group_vars/servers.yml`, specify the disk/partition details for encryption.
    ``` yaml
        partition: /dev/sdc1
     ```

3. **Run the Playbook**:
   ```bash
   ansible-playbook main.yml --ask-become-pass
   ```
   
### Playbook Structure

- **main.yml**: The entry point playbook that calls all the required roles and tasks.
- **roles/cpu_performance**:
  - **tasks**: Contains the individual task files that perform the encryption, CPU configuration, and network interface renaming.
  - **handlers**: Define handlers for triggering changes like restarting services if necessary.
  - **vars**: Define any role-specific variables.
  - **defaults**: Contains the default variables for the role.

### Error Handling

- Tasks has appropriate error handling in place using Ansible's built-in mechanisms such as `ignore_errors`, `failed_when`, and custom task messages.
- Playbook tasks return clear success or failure messages to inform the user of the result.


### Notes

- Ensure that the inventory file is properly configured with the correct partition paths for encryption.
- The playbook assumes you have SSH access to the target servers and that Ansible has the necessary privileges to perform system-level changes.
