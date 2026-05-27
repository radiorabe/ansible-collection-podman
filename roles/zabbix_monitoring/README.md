# Ansible Role - radiorabe.podman.zabbix_monitoring

Configure Zabbix monitoring for RaBe Podman rootless containers.

## Requirements

None

## Role Variables

| Variable | Default | Description |
| -------- | ------- | ----------- |
| `zabbix_monitoring_podman_socket_enabled` | `true` | Ensure the Podman socket is enabled for monitoring |
| `zabbix_monitoring_podman_user` | `not set` | Name of the podman user **required** |
| `zabbix_monitoring_zabbix_user` | `zabbix` | Username used by Zabbix |
| `zabbix_monitoring_zabbix_group` | `{{ zabbix_monitoring_zabbix_user }}` | Primary group for Zabbix user |

## Dependencies

None

## Example Playbook

```yaml
- hosts: all
  gather_facts: false
  roles:
    - role: radiorabe.podman.zabbix_monitoring
      vars:
        zabbix_monitoring_podman_user: testuser
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
