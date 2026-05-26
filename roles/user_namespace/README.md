# Ansible Role - radiorabe.podman.user_namespace

This role creates or configures a local user and assigns `subuid`/`subgid` ranges required for Podman user namespaces.

## Role Variables

- `user_namespace_username`: Username to create or configure.
- `user_namespace_create_home`: Create a home directory for the user.
- `user_namespace_groupname`: Group name for the user.
- `user_namespace_home_directory`: Home directory path.
- `user_namespace_shell`: Login shell for the user.
- `user_namespace_system`: Create a system user.
- `user_namespace_subuid_range`: Subuid range to assign to the user.
- `user_namespace_subgid_range`: Subgid range to assign to the user.

## Dependencies

This role uses `radiorabe.common.local_user` to manage the local user account and assumes the target system can configure `/etc/subuid` and `/etc/subgid` via `usermod`.

## Example Playbooks

```yaml
- name: Configure user namespace for Podman
  hosts: localhost
  gather_facts: false
  roles:
    - role: radiorabe.podman.user_namespace
      vars:
        user_namespace_username: podmanuser
        user_namespace_create_home: true
        user_namespace_groupname: podmanuser
        user_namespace_home_directory: /home/podmanuser
        user_namespace_shell: /bin/bash
        user_namespace_system: false
        user_namespace_subuid_range: "100000-165535"
        user_namespace_subgid_range: "100000-165535"
```

## License

This role is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.
