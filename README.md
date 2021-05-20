# role-jumpcloud

### Master:
- Travis CI: ![TravisCI](https://travis-ci.com/osx-provisioner/role-jumpcloud.svg?branch=master)
- Github Actions: [![role-jumpcloud](https://github.com/osx-provisioner/role-jumpcloud/actions/workflows/push.yml/badge.svg?branch=master)](https://github.com/osx-provisioner/role-jumpcloud/actions/workflows/push.yml)

### Production:
- Travis CI: ![TravisCI](https://travis-ci.com/osx-provisioner/role-jumpcloud.svg?branch=production)
- Github Actions: [![role-jumpcloud](https://github.com/osx-provisioner/role-jumpcloud/actions/workflows/push.yml/badge.svg?branch=production)](https://github.com/osx-provisioner/role-jumpcloud/actions/workflows/push.yml)

Ansible role that installs the JumpCloud agent on OSX machines.

### Notes:
- See the [JumpCloud Website](https://jumpcloud.com/) for further details about this platform.

Requirements
------------

None

Role Variables
--------------

- `jumpcloud_agent_url`:
    - The URL to the JumpCloud Agent installation script for OSX.  (Available from the JumpCloud website.)
- `jumpcloud_uninstall_url`:
    - The URL to the JumpCloud Agent uninstall script for OSX.  (Available from the JumpCloud website, not currently used.)
- `jumpcloud_connect_key:`
    - The preferred method of setting this variable is through the `JUMPCLOUD_CONNECT_KEY` environment variable.
    - The value should be set to your JumpCloud Connect Key, this secret value is accessible from the JumpCloud admin console. 
- `jumpcloud_upgrade`:
    - A boolean which determines if the installer will try to update existing JumpCloud installs.
- `jumpcloud_agent_location`:
    - The expected installation location.
- `jumpcloud_installer_destination`:
    - The ephemeral location for the downloaded installer script.

[See The Default Values](defaults/main.yml)

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: web
  roles:
  - role: osx_provisioner.jumpcloud
    jumpcloud_agent_url: "https://raw.githubusercontent.com/TheJumpCloud/support/master/scripts/macos/install_agent_and_serviceaccount.sh"
    jumpcloud_uninstall_url: "https://github.com/TheJumpCloud/support/releases/download/mac_agent_uninstaller/remove_mac_agent.sh"
    jumpcloud_connect_key: "{{ lookup('env', 'JUMPCLOUD_CONNECT_KEY') }}"
    jumpcloud_upgrade: false
    jumpcloud_agent_location: /opt/jc
    jumpcloud_installer_destination: /tmp/jc_installer.sh
```

License
-------

MPL-2

Author Information
------------------

Niall Byrne <niall@niallbyrne.ca>
