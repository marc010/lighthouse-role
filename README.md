Lighthouse
=========

This role can install lighthouse


Role Variables
--------------

| vars               | description                      |
|--------------------|----------------------------------|
| lighthouse_url     | URL to lighthouse                |
| lighthouse_version | Version of lighthouse to install |


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:


```
- name: Install Lighthouse
  hosts: lighthouse-01
  roles:
    - { role: lighthouse-role }        
```

License
-------

MIT

Author Information
------------------

Ilya T.
