# Ansible Tutorials:

## Introduction
- Ansible is a configuration management and deployment tool that simplifies the process of automating IT tasks. It uses YAML-based configuration files to describe the desired state of systems and then takes the necessary actions to achieve that state.

## Key Concepts
1. Playbooks: These are the core of Ansible. They define the tasks to be executed on a group of hosts.
2. Inventory: This file lists the hosts or groups of hosts that Ansible will manage.
3. Roles: Roles are reusable units of automation that can be included in multiple playbooks.
4. Tasks: Tasks are individual actions that Ansible performs, such as copying files, installing packages, or executing commands.
5. Modules: Modules are the building blocks of Ansible. They provide the functionality for performing specific tasks.
6. Tags: Tags are labels that can be applied to groups of tasks or roles, allowing for selective execution.

## Using Ansible
1. Installation
- Install Ansible on your control machine using the appropriate package manager for your operating system.

2. Inventory File
- Create an inventory file (e.g., hosts) to list the hosts you want to manage:

```YAML
[webservers]
server1 ansible_host=192.168.1.100
server2 ansible_host=192.168.1.101

[databases]
db1 ansible_host=192.168.1.102
```
3. Playbooks
- Create a playbook (e.g., deploy_web_app.yml) to define the tasks:

```YAML
- name: Deploy a Web Application
  hosts: webservers
  tasks:
    - name: Install Apache
      apt: name=apache2 state=present

    - name: Copy web files
      copy: src=./web_files/ dest=/var/www/html/

    - name: Restart Apache
      service: name=apache2 state=restarted
```

4. Execution
- Run the playbook:

```Bash
ansible-playbook deploy_web_app.yml
```

## Real-World Example: Deploying a LAMP Stack
- Create a playbook to deploy a LAMP (Linux, Apache, MySQL, PHP) stack on multiple servers:

```YAML
- name: Deploy LAMP Stack
  hosts: webservers
  roles:
    - lamp
```
```YAML
# lamp.yml (role file)
---
- name: Install LAMP Stack
  tasks:
    - name: Install Apache
      apt: name=apache2 state=present

    - name: Install MySQL
      apt: name=mysql-server state=present

    - name: Install PHP
      apt: name=php7.4   
 state=present

    - name: Configure MySQL
      mysql_user: name=myuser password=mypassword
```

## Ad-Hoc Commands
For quick, one-time tasks, use ad-hoc commands:

```Bash
ansible webservers -m ping
```

## Tags
- Use tags to selectively run tasks:
```YAML
- name: Deploy Web App
  hosts: webservers
  tasks:
    - name: Install Apache
      apt: name=apache2 state=present
      tags: apache

    - name: Copy web files
      copy: src=./web_files/ dest=/var/www/html/
      tags: files
```
- Run the playbook with a specific tag:

```Bash
ansible-playbook deploy_web_app.yml --tags files
```
### Additional Features
- Variables: Use variables to store dynamic values.
- Conditionals: Use conditionals to control task execution based on conditions.
- Loops: Use loops to iterate over lists or dictionaries.
- Inventory Groups: Organize hosts into groups for easier management.
- Ansible Galaxy: Use Ansible Galaxy to share and reuse roles.
By understanding these concepts and following the examples, you can effectively use Ansible to automate your IT infrastructure.

