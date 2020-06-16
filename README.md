# webinar

there would be a playbook to create a VM at DigitalOcean  
  
# installation   
## Ubuntu    
sudo apt update  
sudo apt install software-properties-common  
sudo apt-add-repository --yes --update ppa:ansible/ansible  
sudo apt install ansible  

# Running  
  
ansible-playbook \
- K \  
--vault-password-file ~/secret.key \
--inventory "web1, web2, " \  
--tags "check_api_health" \  
vm_create.yml  
