```
vi pckg.yaml
```
```
---
- name: Installing list of packages
  hosts: all
  become: yes
  tasks:
  - name: install packages
    yum:
     name: "{{ item }}"
     state: present
    # loop or with_items
    with_items:
    - tree
    - curl
    - wget
    - telnet
    - vsftpd
    - dnsutils
    when: ansible_facts['distribution'] == 'CentOS'
```
```
ansible-playbook pckg.yaml
```
