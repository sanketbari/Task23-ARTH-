# Task23-ARTH-
Automate Kubernetes Cluster Using Ansible 
=========================================
What we have to do?
-------------------
🔅 Launch ec2-instances on AWS Cloud eg. for master and slave.  </br>
🔅 Create roles that will configure master node and slave node seperately. </br>
🔅 Launch a wordpress and mysql database connected to it in the respectine slaves.  </br>
🔅 Exposing the wordpress pod and client able hit the wordpress ip with its respective port.</br>

How you can do this?
--------------------

To launch Ec2 Instances you have to use:</br>
      :one: Ec2RoleMaster.yml</br>
      :two: Ec2RoleSlave1.yml</br>
      :three: Ec2RoleSlave2.yml</br>
These above files will launch 3 Ec2 Instances for Master Node and 2 Slave Nodes respectivly.</br>
:bulb: Now you can use setupEc2.yml to launch Ec2 Instances.</br>

:large_orange_diamond: Change in ansible conf(/etc/ansible/ansible.cfg) file in your vm "inventory='your inventory folder'"</br>
:large_orange_diamond: Change "roles-path='path of your role'" in ansible conf file that is /etc/ansible/ansible.cfg</br>
:large_orange_diamond: Change "remote_user='ec2-user'" in ansible conf file that is /etc/ansible/ansible.cfg</br>
:large_orange_diamond: Change "ansible_private_key='path of your key" in ansible conf file that is /etc/ansible/ansible.cfg</br>
:large_orange_diamond: Change permission of your private key by run cmd in bash shell "chmod 400 'key name'"</br>

:milky_way: For dyanamic inventory run following commands in bash shell
-----------------------------------------------------------------------

:pushpin: export AWS_ACCESS_KEY_ID='access-key-id'</br>
:pushpin: export AWS_SECRET_ACCESS_KEY='secret-access-key'</br>
:pushpin: export AWS_REGION='region name'</br>

:sos: MySql pod require us to pass Environment Variables which is passed in the wordpress_Mysql/files/mysqlDeploy.yml File using valueFrom Secrets file which is named as Mysecret.yml.</br>
:round_pushpin:Environment Variables in Mysecret.yml file are encoded with base64 Encoder. You can change the values but make sure you use base64 Encoder.</br>

:large_orange_diamond:<Give your localhost name "ip of the mysql pod">  </br>

:bulb: Now you can use setup.yml to start Kubernetes Configuration.




