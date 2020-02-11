# Deploy kubernetes on servers
## Repository consists of two playbooks:

 `k8s-deploy.yml` - will deploy on your Kubernetes servers on the principle of Master Slave 
 
 `k8s-purge.yml` - will remove Kubernetes on your servers

## In order for playbooks to work, you need to:
  1. Change the inventory file located in the folder `roles/inventory`, specifying your ip in the parameter `ansible_host={{ ip_host }}` 
  2.
    2.1 Throw the public ssh key to your servers with the command:
      `ssh-copy-id -i ssh-key/vm_rsa.pub`
    2.2 Либо сгенероировать свои ключи:
      `ssh-keygen`
       и положить их в дирректорию ssh-key

  3. Потом указать явно ваш приватный ssh ключ командой:
      `eval `ssh-agent -s`; ssh-add ssh-key/vm_rsa`
  
  4. После чего запустить одну из playbook например:
      `ansible-playbook k8s-deploy.yml`


