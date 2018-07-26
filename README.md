# third-party-ci-installer
A ansible Zuul v3 + Nodepool installer

Install Steps:
1. Install requirements
   ```
   sudo apt update
   sudo apt install python3 python3-pip git
   ```
2. Install ansible & required ansible roles from galaxy
   ```
   sudo pip3 install ansible
   ansible-galaxy install geerlingguy.apache
   ansible-galaxy install geerlingguy.mysql
   ```
3. Clone repository
   ```
   git clone https://github.com/CiscoSystems/third-party-ci-installer
   ```
4. Change directory
   ```
   cd third-party-ci-installer
   ```
5. Edit ```localhost_inv.yaml``` to match your environment (Update nodeprovider_ip/username/password/project). If the logserver is on the same server as zuul and nodepool then the services list should include both 'zuul' and 'logserver'
6. Install
   ```
   ansible-playbook -K -i localhost_inv.yaml install.yaml
   ```


NOTE:
If you see an error regarding gearman:
```
TASK [ansible-role-zuul : Install gearman logging file.] ***********************************************************************************************************************************************************************************
fatal: [localhost]: FAILED! => {"changed": false, "checksum": "9222a3bc49518e635aeb3ad9dc4b0e6a9447cd29", "msg": "Unsupported parameters for (copy) module: original_basename Supported parameters include: _original_basename, attributes, backup, checksum, content, delimiter, dest, directory_mode, follow, force, group, local_follow, mode, owner, regexp, remote_src, selevel, serole, setype, seuser, src, unsafe_writes, validate"}  
```
Re-run the ansible playbook
