# ansible

Ansible is a Configuration Management tool which works both on Push and Pull mechanisms.

## INVENTORY File
 1) Inventory is nothing but the list of machine ip or dns names that you want ansible to be managed.
 2) Ansible by default installs 2.9 as by default on AMI's we will get python2. Always go with latest version, which can be installed from tools/ansible/install.sh
3) "all" is a group which included all the entries in INVENTORY File.

### Ansible is all about modules( collections )----recently they statrted calling them as collections

ANSIBLE has lot of pre-defined variables and we need to use them to supply userName and password it has to use to authenticate to the nodes.

ans
### ansible_user     : Predefined variable for userName 
### ansible_password : Predefined variable for password  
Variables should be passed to ansible by using the flag -e

    Ex: ansible -i INVENTORY all  -e ansible_user=userName -e ansible_password=password 
    $ ansible -i inv all  -e ansible_user=centos -e ansible_password=xyz123 -m shell -a uptime  >(in order to know the  uptime of all servers)


### Automated Approach : This uses Playbook


Playbooks are written using a language called YAML.

YAML is just  markup languaga ; Markup language is nothing but a presentation language.

YAML is indendation specific.

### What is a playbook ?


* Playbook : A Playbook is a list of plays ( and that's why it always starts with - )
* Play     : A Play is a list of tasks.
* Task     : A Task is nothing but an action that we wish to perform

What is a fact ?
In ansible, fact is the property of the node mentioned in the inventory file. By default, ansible is going to gather all the facts of the amchines mentioned in the inventory file

    $ ansible -i inv all -e ansible_user=centos -e ansible_password=abc@123 -m setup
