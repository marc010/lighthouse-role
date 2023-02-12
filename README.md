Lighthouse
=========

This role can install lighthouse

Requirements
 ------------

* nginx;
* git;


Role Variables
--------------

| vars               | description                      |
|--------------------|----------------------------------|
| lighthouse_url     | URL to lighthouse                |
| lighthouse_version | Version of lighthouse to install |
| lighthouse_dir     | Path to lighhouse files          |


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lighthouse-role }

```
- name: Install Lighthouse
  hosts: lighthouse-01
  handlers:
    - name: Start nginx service
      become: true
      ansible.builtin.service:
        name: nginx
        state: restarted
  prt_task:
    - name: Install required packages
      become: true
      ansible.builtin.yum:
        name:
          - epel-release
          - git
        state: present
      tags:
        - install
    - name: Install nginx
      become: true
      ansible.builtin.yum:
        name:
          - nginx
        state: present
      tags:
        - install
    - name: Setup nginx config
      become: true
      ansible.builtin.template:
        src: ./templates/nginx.conf
        dest: /etc/nginx/nginx.conf
        mode: '0644'
      notify: Start nginx service
      tags:
        - install
      roles:
         - { role: lighthouse-role }
```

License
-------

MIT

Author Information
------------------

Ilya T.
