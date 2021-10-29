# postfix

## Description
Role to install and configure samba.

## Example Playbook
```YAML
---
- name: Samba
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: bubebyte.samba
```

## Role Variables
These are the role default which are set in default/main.yml:
```YAML
---
samba_smb_conf:
  global:
    workgroup: SAMBA
    security: user
    'passdb backend': tdbsam
    printing: cups
    'printcap name': cups
    'load printers': true
    'cups options': raw
  homes:
    comment: 'Home Directories'
    'valid users': '%S, %D%w%S'
    browseable: false
    'read only': false
    'inherit acls': true
  printers:
    comment: 'All Printers'
    path: /var/tmp
    printable: true
    'create mask': '0600'
    browseable: false
  'print$':
    comment: 'Printer Drivers'
    path: /var/lib/samba/drivers
    write list: '@printadmin root'
    force group: '@printadmin'
    'create mask': '0664'
    'directory mask': '0775'
```

## Requirements

### Roles
none

### Collections
none

## License
MIT License

## Author Information
[Armin Bube](https://bubebyte.de)
