ansible webservers -i inventory_prod -m user -a "name={{username}} password=12345" --sudo
ansible webservers -i inventory_prod -m ping 
ansible_doc -l
ansible-doc yum
ansible webservers -i inventory_prod -m yum -a "name=httpd state=present"
ansible webservers -i inventory_prod -m yum -a "name=httpd state=present" --sudo
vagrant@acs:~/exercise4.3/production$ ansible dbservers -i inventory_prod -m yum -a "name=mysql-server state=present" --sudo


sudeep@sudeep:~/Projects/Learning/practicesources/hands-on-ansible$ vagrant ssh db
Last login: Fri Oct 26 05:09:27 2018 from 192.168.33.10
Welcome to your Vagrant-built virtual machine.
[vagrant@db ~]$ service mysqld status
mysqld: unrecognized service
[vagrant@db ~]$ service mysqld status
mysqld is stopped
[vagrant@db ~]$ service mysqld status


//start mysqld service on db server
ansible dbservers -i inventory_prod -m service -a "name=mysqld  state=started" --sudo
ansible dbservers -i inventory_prod -m service -a "name=mysqld  state=started" --sudo
vice -a "name=mysqld  state=started" --sudo
db1 | success >> {
    "changed": true, 
    "name": "mysqld", 
    "state": "started"
}

//stop firewall to access db and web servers

 ansible webservers:dbservers -i inventory_prod -m service -a "name=iptables state=stopped" --sudo
db1 | success >> {
    "changed": true, 
    "name": "iptables", 
    "state": "stopped"
}

web1 | success >> {
    "changed": true, 
    "name": "iptables", 
    "state": "stopped"


//setup module
 ansible web1 -i inventory_prod -m setup

 returned all data realted to system

ansible web1 -i inventory_prod -m setup -a "filter=ansible_eth*"

ansible web1 -i inventory_prod -m setup -a "filter=ansible_mounts"
web1 | success >> {
    "ansible_facts": {
        "ansible_mounts": [
            {
                "device": "/dev/mapper/VolGroup-lv_root", 
                "fstype": "ext4", 
                "mount": "/", 
                "options": "rw", 
                "size_available": 194706022400, 
                "size_total": 206629191680
            }, 
            {
                "device": "/dev/sda1", 
                "fstype": "ext4", 
                "mount": "/boot", 
                "options": "rw", 
                "size_available": 448076800, 
                "size_total": 507744256
            }
        ]
    }, 
    "changed": false
}



vagrant@acs:~/excercise_6.2$ ls
ansible.cfg  inventory_prod  web_db


inventory specied in ansible.cfg no need to provide -i switch

ansible-playboook web_db.yml

ansible-playboook web_db.yml --limit @home/vagrant/web_db.retry to run for failed taskls

playbook handlers

jinja2  - change static file to dynamic file
