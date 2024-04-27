# Devops:

## Git Folder

> git add .;git commit -m "nginx playbook"; git push

## Ansible Folder
**AWS instnce Launch:**
Communit edition of RHEL9

 *UserName :* ec2-user <br />
 *password:* DevOps321

 **Ansible Intro:**
 1. It is a configuration managemnet tool.
 2. It follows PUSH based mechanism about most use-case.
    Unlike, Chef & puppet are PULL based.
 3. Configuration Mangement tools follow the CRUD opertaions.

**Ansible ADHOC Commands:**

Linux --> commands <br />
Ansible --> Modules/collections

> ansible -i \<inventory> -e ansible_user=user_name -e ansible_password=password
> <br />
> <br />
> ansible -i 54.92.202.148, all -e anisble_user=ec2-user -e ansible_password=DevOps321 -m ping

**Note:** Make sure in real-world, ansible master node connects with remote nodes via SSH <br />
--> Open port 22 on remote nodes <br />
--> security groups configured

**ansible package installation CMD:**

> ansible -i 54.92.202.148, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -m dnf -a "name=nginx state=installed" -b

**Note:** -b is kind of sudo/root access to install, -a is arguments

Start the NGINX service:
> ansible -i 54.92.202.148, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -m service -a "name=nginx state=started" -b

**Debug logs:** -vvv 

> ansible -i 54.92.202.148, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -m dnf -a "name=nginx state=installed" -b -vvv


**PlayBooks**

Keep all your modules/collections in a single YAML file.

**YAML:** Follows the indentation - Yet Another Markup Language/YAML

**Ansible Playbook Folder structure:**

1. playbook_name.yaml/ playbook_name.yml
2. inventory.ini

**tasks:** nothing but tasks/modules/collections

> ansible -i inventory.ini all --list-hosts
<br />
> ansible -i inventory.ini web --list-hosts

Playbook commands start with `ansible-playbook`:

> ansible-playbook -i inventory.ini -e ansible_user=ec2-user -e anisble_password=DevOps321 01-Ping.yaml

playbook for Nginx:

> ansible-playbook -i inventory.ini -e ansible_user=ec2-user -e anisble_password=DevOps321 02-nginx.yaml
<br />
> ansible -i 54.92.202.148, all  -e anisble_user=ec2-user -e ansible_password=DevOps321 -m shell -a "systemctl status nginx"













