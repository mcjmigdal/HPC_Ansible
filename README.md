# About
This is ansible configuration for a computing cluster with entry node and 3 computing nodes

The configuration implements:

1. Users groups and accounts management.
2. Shared /home directory via NFS.
3. Slurm Workload Manager for queuing system.
4. RStudio Server on one of the nodes outside the queue.

# Testing

1. Bring up VMs

`vagrant up`

2. Log into headnode

`vagrant ssh fisherman`

3. Generate ssh keys and distribute to computing nodes

```
ssh-keygen
cat .ssh/id_rsa.pub >> .ssh/authorized_keys
scp .ssh/id_rsa.pub 10.0.0.43:~/.ssh/authorized_keys
scp .ssh/id_rsa.pub 10.0.0.44:~/.ssh/authorized_keys
scp .ssh/id_rsa.pub 10.0.0.45:~/.ssh/authorized_keys
```

4. Clone repository to VM headnode

`git clone https://github.com/mcjmigdal/HPC_Ansible.git`

5. Run ansible playbook

```
cd HPC_Ansible/ansible/
ansible-playbook main.yml
```

# Setup

1. Configure files in ansible/vars
2. Install ansible on headnode (eg. `pip install ansible`)
3. Clone repository to headnode
4. Run ansible playbook (`ansible-playbook main.yml`)
