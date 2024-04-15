Host patterns in Ansible define the set of target hosts or groups of hosts on which you want to execute tasks. Understanding host patterns is crucial for effective targeting and management of your infrastructure with Ansible.

These examples demonstrate different ways to use host patterns in Ansible to define the scope of your playbooks and ad-hoc commands based on hostnames, groups, intersections, unions, exclusions, and patterns.

Here are some examples of host patterns along with detailed descriptions:

All Hosts:

Pattern: all or *

Description: Targets all hosts in your inventory.

Example:

---
- name: Run on all hosts
  hosts: all
  tasks:
    - name: Execute a task
Specific Host:

Pattern: hostname or ip-address

Description: Targets a specific host by its hostname.

Example:

---
- name: Run on a specific host
  hosts: webserver1/192.168.100.10
  tasks:
    - name: Execute a task
Hosts in a Group:

Pattern: group_name

Description: Targets all hosts belonging to a specific group.

Example:

---
- name: Run on hosts in a group
  hosts: webservers
  tasks:
    - name: Execute a task
Pattern Matching:

Pattern: pattern*

Description: Targets hosts that match a specified pattern using wildcards (*).

Example:

---
- name: Run on hosts with a pattern
  hosts: app*
  tasks:
    - name: Execute a task
Multiple Groups (Union):

Pattern: group1:group2

Description: Targets hosts that are members of either group1 or group2.

Example:

---
- name: Run on hosts in multiple groups
  hosts: db_servers:app_servers
  tasks:
    - name: Execute a task
Intersection of Groups:

Pattern: group1:&group2

Description: Targets hosts that are members of both group1 and group2.

Example:

---
- name: Run on hosts in the intersection of groups
  hosts: webservers:&production
  tasks:
    - name: Execute a task
Numeric Range with Hostnames: If your hostnames follow a pattern, and you want to target hosts with specific numeric values, you can use a numeric range in the hostname. For example:

---
- name: Run on hosts with numeric range
  hosts: webservers[0:1]
  tasks:
    - name: Execute a task
Last Host with Negative Index: If you want to target the last host in a group, you can use [-1] as a slice:

---
- name: Run on last host
  hosts: webservers[-1]
  tasks:
    - name: Execute a task
