# ansible_stuff
Location to place Ansible related files

Ansible dot SSH configuration
Path: ~/.ansible/ssh.config
```
Host <hostname>
    User                   <user_id>
    HostName               <hostname>
    ProxyCommand           none
    IdentityFile           /home/<user_id>/.ssh/id_rsa
    BatchMode              yes
    PasswordAuthentication no
 
Host *
    ServerAliveInterval    60
    TCPKeepAlive           yes
    ProxyCommand           ssh -q -A <hostname> nc %h %p
    User <user_id>
    IdentityFile /home/<user_id>/.ssh/id_rsa
```

Ansible dot config
Path: ~/.ansible.cfg
```
[defaults]
hosts = *
inventory = /home/<user_id>/ansible/inventory
forks = 50
gathering = smart
roles_path = /home/<user_id>/ansible/roles
host_key_checking = False
sudo_flags = -H -S -n
remote_user = <user_id>
ansible_managed = Ansible managed: {file} modified on %Y-%m-%d %H:%M:%S by {uid} on {host}
retry_files_enabled = True
retry_file_save_path=~/.ansible-retry/
 
[ssh_connection]
ssh_args = -o ServerAliveInterval=30 -F /home/<user_id>/.ansible/ssh.config -q
scp_if_ssh = True
```

environmental variables:
```
- name: Get path
  become: False
  shell: |
    echo "$PATH" 
  args:
    executable: /bin/bash
  environment:
    BASH_ENV: "{{ ansible_env['HOME'] }}/.bashrc"
    ```
    
### Molecule setup RHEL 7
subscription-manager repos --enable=rhel-7-server-rpms --enable=rhel-7-server-optional-rpms --enable=rhel-7-server-extras-rpms.
yum install -y gcc python3-pip python3-devel openssl-devel python3-libselinux
yum install docker device-mapper-libs device-mapper-event-libs
yum install python-virtualenv.noarch
