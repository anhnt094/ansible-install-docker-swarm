Description
=========

Install docker. 
Allow firewall to only swarm nodes if swarm_mode is set to TRUE.

Creating role
----------------


    ansible-galaxy init docker-for-centos



Using with playbook
----------------


    - hosts: all
      vars:
        list_of_ips: "{{ groups['all'] | map('extract', hostvars, ['ansible_default_ipv4', 'address']) | join(',') }}"
      
      roles:
         - { role: docker-for-centos, swarm_mode: true, all_hosts: "{{ list_of_ips }}", local_ip: "{{ groups[_group_names[0]] }}" }

Host defilement example
----------------

    [machine-2]
    192.168.122.98
    
    [machine-2:vars]
    ansible_ssh_user=root
    ansible_ssh_pass=1
    
    [centos-7]
    192.168.122.40
    
    [centos-7:vars]
    ansible_ssh_user=root
    ansible_ssh_pass=1
