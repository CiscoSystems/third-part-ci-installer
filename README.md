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
6. Install zuul & nodepool
   ```
   ansible-playbook -K install-zuulnodepool.yaml -e 'ansible_python_interpreter=/usr/bin/python3'
   ```
7. Install logserver
   ```
   ansible-playbook -K install-logserver.yaml
   ```
