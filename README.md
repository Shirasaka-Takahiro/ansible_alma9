# This is an Ansible repository for wordpress

# What this repository contains
1. common(yum update,swap,SELinux,firewalld,hostname,Timezone,useradd) 
2. httpd
3. Nginx
4. MySQL
5. PHP
6. Zabbix-agent
7. Docker

# How to run
1. Copy private key to a file in kyes directroy 
2. Change group_vars,user,Keys,playbook.yml,hosts,vhosts
3. Dry run with "ansible-playbook --private-key {PATH} -i {PATH} hosts {PATH} -C"
4. Run with "ansible-playbook --private-key {PATH} -i {PATH} hosts {PATH}"

#Create ansible exec user
useradd ansible-user
vi /etc/sudoers.d/ansible-user
ansible-user ALL=(ALL) NOPASSWD:ALL
su ansible-user
cd ~
ssh-keygen -p -m PEM -f id_rsa
cd ~/.ssh
cat ./id_rsa.pub > ./authorized_keys
chmod 600 ./authorized_keys

# EXAMPLE
ansible-playbook --private-key /home/takahiro/ansible/ansible_alma9/keys/user.key -i /home/takahiro/ansible/ansible_alma9/hosts /home/takahiro/ansible/ansible_alma9/playbook.yml

ansible-playbook --private-key /home/takahiro/.ssh/private_key -i /home/takahiro/ansible/ansible_alma9/hosts /home/takahiro/ansible/ansible_alma9/playbook.yml