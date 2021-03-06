# IPMU-Cluster
Deployment scripts for GPU cluster @ IPMU. Full cluster documentation can be read at this link: https://docs.google.com/document/d/1O7FO8YwwyP36FeKcwz9bk619vfWf8BBXD5w6jNih_3w/edit?usp=sharing

* `ansible_host_file/hosts` should be placed at `/etc/ansible/hosts` on `neutrino01`.
* make changes to the .yml files (Uses the YAML human-readable language). Everything is controlled by the `update.yml` file.
* to update changes, do `source run_playbook.sh` as the root user. It will ask you to input the root password again to access the other nodes.
* `ansible` scripts define the desired state of the systems, so each time the playbook is run, it will make sure all systems meet the requirements; it will not reinstall the software each time, only install missing packages/users etc
* for example, update `software.yml` to list the packages that must be installed on the machines.
* to add a new user, append their information to `users.yml`, then run `run_playbook.sh` as described above to enforce these changes across the cluster.
* to configure the nodes in other ways, edit `config.yml` (for example, editing startup scripts etc)


## Starting the condor demons on all nodes
The script `start_condor.sh` will turn off HTCondor (if running) and then start all demons again across the cluster.