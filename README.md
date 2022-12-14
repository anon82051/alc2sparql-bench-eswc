# Supplementary material for the paper: "A Recursive Evaluation of SPARQL Queries Accelerates Class Expression Learning"

# Ansible
To set up the experiments we provide an Ansible playbook.

Installation: https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html

# Before running the playbook
 - Replace ```<ip_of_host>``` in ```ansible_playbook/inventory.yaml``` with the IP of the managed node (i.e., the server that will run the experiments).
 - Replace ```<target_dir>``` in ```ansible_playbook/roles/base/defaults/main.yaml``` with the absolute path to the directory of the managed node that will store the experiments' required files.
 - Replace ```<user>``` in ```ansible_playbook/roles/base/defaults/main.yaml``` with the username that will be used to login with to the managed node.
 - Install docker in the server that will run the experiments (https://docs.docker.com/engine/install/debian/) (Note: The user must be added to the docker group)

# GraphDB
In order to run the playbook, a license of GraphDB's free version is required. Please download GraphDB-free 10.0.2 and place the file ```graphdb-10.0.2-dist.zip``` in the directory ```ansible_playbook/graphdb/files```

# Playbook Execution
You can execute the playbook by issuing the following command:

    ansible-playbook -kKi inventory.yaml playbook.yaml

# Benchmark Execution
Before running the benchmarks:

- increase ulimit
    
        ulimit -n 64000

- set swappiness to 0

        sysctl vm.swappiness=0
    
- prepare the databases   
       
        cd <target_dir>
        sudo ./run-loaders.sh

To run the benchmark execute the script ```run_sparql.sh``` with root privileges.

    cd <target_dir>
    sudo ./run-sparql.sh
The results  of the benchmark (IGUANA result files) are stored in the directory `<target_dir>/iguana_results/sparql`

# Datasets and Queries
The datasets used in the benchmark and their respective queries are available online: https://www.dropbox.com/scl/fo/8bvt9b296brbwet171li5/h?dl=0&rlkey=ai1atekz4zez8wlbys6zgqkcg

# Results
The results presented in the paper are available in `results.zip`.