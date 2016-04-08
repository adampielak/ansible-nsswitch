nsswitch
========

Role which helps to manage the nsswitch.conf file.


Example
-------

```
---

# Default usage
- hosts: myhost1
  roles:
    - nsswitch

# Example of how to add a new option to a database
- hosts: myhost2
  vars:
    # Add 'sss' option to the groups database
    nsswitch_group__custom:
      - sss
  roles:
    - nsswitch

# Example of how to suppress some of the database
- hosts: myhost3
  vars:
    # Set value to empty list to suppress a database
    nsswitch_bootparams: []
  roles:
    - nsswitch

# Example of how to add an additional database
- hosts: myhost4
  vars:
    # Definition of the new database
    nsswitch__custom:
      customdb:
        - files
  roles:
    - nsswitch

# Example of how to redefine the configturation from scratch
- hosts: myhost5
  vars:
    # The new nsswitch config will contain only passwd, shadow, group and
    # hosts databases
    nsswitch_config:
      passwd: "{{ nsswitch_passwd }}"
      shadow: "{{ nsswitch_shadow }}"
      group: "{{ nsswitch_group }}"
      hosts: "{{ nsswitch_hosts }}"
  roles:
    - nsswitch
```


Role variables
--------------

List of variables used by the role:

```
# Default location of the config file
nsswitch_file_location: /etc/nsswitch.conf


# Default aliases
nsswitch_aliases__default:
  - files
  - nisplus

# Custom aliases
nsswitch_aliases__custom: []

# Final aliases
nsswitch_aliases: "{{
  nsswitch_aliases__default +
  nsswitch_aliases__custom }}"


# Default automount
nsswitch_automount__default:
  - files
  - nisplus

# Custom automount
nsswitch_automount__custom: []

# Final automount
nsswitch_automount: "{{
  nsswitch_automount__default +
  nsswitch_automount__custom }}"


# Default bootparams
nsswitch_bootparams__default:
  - nisplus
  - '[NOTFOUND=return]'
  - files

# Custom bootparams
nsswitch_bootparams__custom: []

# Final bootparams
nsswitch_bootparams: "{{
  nsswitch_bootparams__default +
  nsswitch_bootparams__custom }}"


# Default ethers
nsswitch_ethers__default:
  - files

# Custom ethers
nsswitch_ethers__custom: []

# Final ethers
nsswitch_ethers: "{{
  nsswitch_ethers__default +
  nsswitch_ethers__custom }}"


# Default group
nsswitch_group__default:
  - files

# Custom group
nsswitch_group__custom: []

# Final group
nsswitch_group: "{{
  nsswitch_group__default +
  nsswitch_group__custom }}"


# Default hosts
nsswitch_hosts__default:
  - files
  - dns

# Custom hosts
nsswitch_hosts__custom: []

# Final hosts
nsswitch_hosts: "{{
  nsswitch_hosts__default +
  nsswitch_hosts__custom }}"


# Default initgroups
nsswitch_initgroups__default:
  - files

# Custom initgroups
nsswitch_initgroups__custom: []

# Final initgroups
nsswitch_initgroups: "{{
  nsswitch_initgroups__default +
  nsswitch_initgroups__custom }}"


# Default netgroup
nsswitch_netgroup__default:
  - nisplus

# Custom netgroup
nsswitch_netgroup__custom: []

# Final netgroup
nsswitch_netgroup: "{{
  nsswitch_netgroup__default +
  nsswitch_netgroup__custom }}"


# Default netmasks
nsswitch_netmasks__default:
  - files

# Custom netmasks
nsswitch_netmasks__custom: []

# Final netmasks
nsswitch_netmasks: "{{
  nsswitch_netmasks__default +
  nsswitch_netmasks__custom }}"


# Default networks
nsswitch_networks__default:
  - files

# Custom networks
nsswitch_networks__custom: []

# Final networks
nsswitch_networks: "{{
  nsswitch_networks__default +
  nsswitch_networks__custom }}"


# Default passwd
nsswitch_passwd__default:
  - files

# Custom passwd
nsswitch_passwd__custom: []

# Final passwd
nsswitch_passwd: "{{
  nsswitch_passwd__default +
  nsswitch_passwd__custom }}"


# Default protocols
nsswitch_protocols__default:
  - files

# Custom protocols
nsswitch_protocols__custom: []

# Final protocols
nsswitch_protocols: "{{
  nsswitch_protocols__default +
  nsswitch_protocols__custom }}"


# Default publickey
nsswitch_publickey__default:
  - nisplus

# Custom publickey
nsswitch_publickey__custom: []

# Final publickey
nsswitch_publickey: "{{
  nsswitch_publickey__default +
  nsswitch_publickey__custom }}"


# Default rpc
nsswitch_rpc__default:
  - files

# Custom rpc
nsswitch_rpc__custom: []

# Final rpc
nsswitch_rpc: "{{
  nsswitch_rpc__default +
  nsswitch_rpc__custom }}"


# Default services
nsswitch_services__default:
  - files

# Custom services
nsswitch_services__custom: []

# Final services
nsswitch_services: "{{
  nsswitch_services__default +
  nsswitch_services__custom }}"


# Default shadow
nsswitch_shadow__default:
  - files

# Custom shadow
nsswitch_shadow__custom: []

# Final shadow
nsswitch_shadow: "{{
  nsswitch_shadow__default +
  nsswitch_shadow__custom }}"


# Default list of (all) databases
nsswitch__default:
  aliases: "{{ nsswitch_aliases }}"
  automount: "{{ nsswitch_automount }}"
  bootparams: "{{ nsswitch_bootparams }}"
  ethers: "{{ nsswitch_ethers }}"
  group: "{{ nsswitch_group }}"
  hosts: "{{ nsswitch_hosts }}"
  initgroups: "{{ nsswitch_initgroups }}"
  netgroup: "{{ nsswitch_netgroup }}"
  netmasks: "{{ nsswitch_netmasks }}"
  networks: "{{ nsswitch_networks }}"
  passwd: "{{ nsswitch_passwd }}"
  protocols: "{{ nsswitch_protocols }}"
  publickey: "{{ nsswitch_publickey }}"
  rpc: "{{ nsswitch_rpc }}"
  services: "{{ nsswitch_services }}"
  shadow: "{{ nsswitch_shadow }}"

# Custom list of databases
nsswitch__custom: {}

# Final configuration
nsswitch_config: "{{
  nsswitch__default.update(nsswitch__custom) }}{{
  nsswitch__default }}"
```


License
-------

MIT


Author
------

Jiri Tyr
