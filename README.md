# Ansible Role: sysctl

This role configures sysctl (kernel) parameters on your Linux distribution.

## Requirements

This role was developed and tested with the following Ansible versions:

| Name                                                   | Version         |
|--------------------------------------------------------|-----------------|
| [ansible](https://pypi.org/project/ansible/)           | ```>= 2.9.9```  |

Other Ansible versions were not tested, but will probably work.

## Installation

Use ```ansible-galaxy install igor_nikiforov.sysctl``` to install the latest stable release of role.

You could also install it from requirements ```ansible-galaxy install -r requirements.yml```:

```yaml
# requirements.yml
---
roles:
  - name: igor_nikiforov.sysctl
    version: v1.0.0
```

## Usage

Role supports all sysctl configuration parameters. Please use ```sysctl -a``` to print all possible parameters.

### Examples

```yaml
# playbook.yml
---
- hosts: all
  become: true
  gather_facts: false

  pre_tasks:
    - wait_for_connection: { timeout: 300 }
    - setup:

  vars:
    sysctl_settings:
      - name: net.ipv4.ip_forward
        value: 1

  tasks:
    - name: Configure sysctl parameters
      import_role:
        name: sysctl
```

## License

MIT

## Author Information

[Igor Nikiforov](https://github.com/igor-nikiforov)
