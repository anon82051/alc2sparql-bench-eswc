# Supplementary material for the paper: "A Recursive Evaluation of SPARQL Queries Accelerates Class Expression Learning"

# Ansible
To set up the experiments we provide an Ansible playbook.

Installation: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

# Before running the playbook
 - Replace ```<ip_of_host>``` in ```ansible_playbook/inventory.yaml``` with the IP of the managed node (i.e., the server that will run the experiments).
 - Replace ```<target_dir>``` in ```ansible_playbook/roles/base/defaults/main.yaml``` with the path to the directory of the managed node that will store the experiments' required files.
 - Replace ```<user>``` in ```ansible_playbook/roles/base/defaults/main.yaml``` with the username that will be used to login with to the managed node.
 - Install docker in the server that will run the experiments (https://docs.docker.com/engine/install/debian/)

# GraphDB
In order to run the playbook, a license of GraphDB's free version is required. Replace ```<path-to-graphdb-zip>``` in ```ansible_playbook/roles/graphdb/tasks/install.yaml``` with the path to your local copy of GraphDB 10.0.2.

# Playbook Execution
You can execute the playbook by issuing the following command:

    ansible-playbook -kKi inventory.yaml playbook.yaml
