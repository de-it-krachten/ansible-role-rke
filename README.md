[![CI](https://github.com/de-it-krachten/ansible-role-rke/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-rke/actions?query=workflow%3ACI)


# ansible-role-rke

Installs Rancher Kubernetes Engine (RKE)<br>
https://www.rancher.com/products/rke<br>



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 40
- Fedora 41

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Github CLI - API
rke_api: https://api.github.com/repos/rancher/rke

# Github CLI - repo
rke_repo: https://github.com/ranche/rke

# Lookup table for architecture
rke:
  architecture:
    x86_64: amd64
    i386: i386
    armv6l: arm
    armv7l: arm
    aarch64: arm64
  system:
    Linux: linux
    Darwin: darwin

# Construct filename based on the system & architecture
rke_file: "rke_{{ rke_system }}-{{ rke_architecture }}"

# Version of the CLI to install
rke_version: latest

# Location/ownership/permissions of the binary
rke_path: /usr/local/bin/rke
rke_owner: root
rke_group: root
rke_mode: '0755'
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'rke'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'rke'
      ansible.builtin.include_role:
        name: rke
</pre></code>
