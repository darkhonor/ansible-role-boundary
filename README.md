# Boundary Server

This role installs the HashiCorp Boundary server. Variations of the role will
allow for both server build as well as Boundary Agent deployment.

## Requirements

There are no pre-requisite requirements for this role.  The variables set below
will help to localize the installation.

## Role Variables

The following variables are available in this role.  The default values
are shown here:

```yaml
airgap: false
hashicorp_rpm_repo_url: https://rpm.releases.hashicorp.com/RHEL/$releasever/$basearch/stable
hashicorp_gpg_key_url: https://rpm.releases.hashicorp.com/gpg
trust_repository_certs: true
enable_service: true
service_state: started
bind_addr: "0.0.0.0"
enable_tls: true
```

## Dependencies

N/A

## Example Playbook

Here is an example use of this role in for a system that is Internet-connected:

```yaml
- name: Install and Configure HashiCorp Boundary
  become: true
  gather_facts: true
  hosts: servers
  roles:
    - role: boundary
```

Here is an example for a system that is in an airgap environment:

```yaml
- name: Install and Configure HashiCorp Boundary
  become: true
  gather_facts: true
  hosts: servers
  roles:
    - role: boundary
      airgap: true
      hashicorp_rpm_repo_url: "https://repo.network.local/hashicorp/"
      hashicorp_gpg_key_url: "https://repo.network.local/certs/hashicorp.gpg"
```

## License

MIT

## Author Information

Alex Ackerman, GitHub @darkhonor
