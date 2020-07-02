# webinar

there would be a playbook to create a VM at DigitalOcean  
  
# installation   
## Ubuntu    
sudo apt update  
sudo apt install software-properties-common  
sudo apt-add-repository --yes --update ppa:ansible/ansible  
sudo apt install ansible  

# Running  
   
 
This allows you to get list of locations  
and available to deploy sizes and features of VMs on Digital Ocean:  
```
ansible-playbook \
--vault-password-file ~/secret.key \
do_get_regions.yml  
```
  
Create VMs:
```
ansible-playbook \
-K \
--vault-password-file ~/secret.key \
--inventory "web1, web2, " \
vm_create.yml
```
  
Create VMs with specified resources and image:  
```
ansible-playbook \
-K \
--vault-password-file ~/secret.key \
--inventory "web1, " \
--extra-vars "size='{{ sizes.medium }}' image='{{ images.ub1604 }}'" \
vm_create.yml
```
  
Update, upgrade, install software:
```
ansible-playbook \
-u root \
--vault-password-file ~/secret.key \
--inventory "web1, " \
software_install.yml
```

Destroy VMs:
```
ansible-playbook \
-K \
--vault-password-file ~/secret.key \
--inventory "web1, web2, " \
vm_destroy.yml
```
  
Destroy all VMs by a tag:  
```
ansible-playbook \
-K \
--vault-password-file ~/secret.key \
--extra-vars "vm_tag=webinar1" \
vm_destroy_by_tag.yml
```