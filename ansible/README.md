# Ansible Script for Setting a Server Up

## Installation

1. Spin-up an Ubuntu server on AWS (or any other hosting)
1. Edit the IPs of the server in the provided `hosts` file (present at the 
same level as this README). Please make sure to indicate **public** IP.
1. In AWS EC2, the root username for Ubuntu servers is called: `ubuntu`. If you 
   spin your servers up somewhere where that is not the case, edit 
   `group_vars/all.yml` and modify the value of the `ansible_ssh_user: ubuntu` variable.
1. Create `ssh` folder under this checkout (same level as README)
1. Save a private SSH key that corresponds to the root user on all your new servers
   under: `ssh/private-key.pem`
1. Make sure your private key permissions are valid:
       
       ```consul
       chmod 700 ssh
       chmod 600 ssh/*
       ```
## Quickstart

To make sure your ssh and hosts setup is correct and you can login to all 
required servers:

```console
ansible all -m ping -i hosts
```

To install basic Linux tools (curl, vim etc.) on all servers:

```console
ansible-playbook baseline.yml -i hosts
```

To install entire infrastructure:

```console
ansible-playbook bootstrap.yml -i hosts
```