# third-party-ci-installer
A ansible Zuul v3 + Nodepool installer

Install Steps:
1. Install requirements
   ```
   sudo apt install python3 python3-pip git
   ```
2. Install ansible & required ansible roles from galaxy
   ```
   sudo pip3 install ansible
   ansible-galaxy install geerlingguy.apache
   ```
3. Clone repository
   ```
   git clone https://github.com/CiscoSystems/third-party-ci-installer
   ```    
4. Change directory
   ```
   cd third-party-ci-installer
   ```
5. Make any necessary config changes in ```files/*```
6. Edit ```localhost_inv.ini``` to match your environment. (Update nodeprovider_ip/username/password/project)
7. Install zuul & nodepool
   ```
   ansible-playbook -K -i localhost_inv.ini install-zuulnodepool.yaml -e 'ansible_python_interpreter=/usr/bin/python3'
   ```
8. Install logserver
   ```
   ansible-playbook -K install-logserver.yaml
   ```
