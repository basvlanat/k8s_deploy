# Deploy kubernetes on servers
## Repository consists of two playbooks:

 `k8s-deploy.yml` - will deploy on your Kubernetes servers on the principle of Master Slave 
 
 `k8s-purge.yml` - will remove Kubernetes on your servers

## In order for playbooks to work, you need to:
  1. Change the inventory file located in the folder `roles/inventory`, specifying your ip in the parameter `ansible_host={{ ip_host }}` 
  2.
    2.1 Throw the public ssh key to your servers with the command:
      `ssh-copy-id -i ssh-key/vm_rsa.pub`
    2.2 Or generate your keys:
      `ssh-keygen`
       and put them in the ssh-key directory

  3. Then explicitly specify your private ssh key with the command:
      `eval `ssh-agent -s`; ssh-add ssh-key/vm_rsa`
  
  4. Then start one of the playbook for example:
      `ansible-playbook k8s-deploy.yml`


