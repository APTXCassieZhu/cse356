# cse356
hw1

---
- name: cse356hw1
  hosts: hw1
  gather_facts: no
  remote_user: ubuntu
  become: true
  become_method: sudo
  tasks:
          - name: Create a new directory
            file:
                    path: /cse356hw0
                    state: directory
          - name: Install Apache
            apt: name=apache2 update_cache=yes state=latest
          - name: Pull HW0 from git
            git:
                    repo: 'https://github.com/APTXCassieZhu/cse356hw1'
                    dest: /cse356hw0
          - name: move hw0.html
            command: mv /cse356hw0/hw0.html /var/www/html

