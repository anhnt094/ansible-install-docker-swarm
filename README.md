Role Name
=========

Install docker. 
Allow firewall to only swarm nodes if swarm_mode is set to TRUE.


Using with playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      vars:
        list_of_ips: "{{ groups['all'] | map('extract', hostvars, ['ansible_default_ipv4', 'address']) | join(',') }}"
      
      roles:
         - { role: docker-for-centos, swarm_mode: true, all_hosts: "{{ list_of_ips }}" }

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
