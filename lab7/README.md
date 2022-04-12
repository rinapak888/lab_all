We have the following tasks: configure the consul (use a ready-made role and inventory), the database must be initialized on dedicated disks (they are already connected in Vargrantfile).

The database should be located in the folder /pgsql/pg_data/14. WAL archives should be located in the folder /pgsql/pg_wal/14. The /dev/sdb and /dev/sdc disks must be mounted in these folders.

The disks must be mounted in LVM and formatted in the xfs file system.

On pg1 and pg2 servers, configure the Patroni replication orchestrator (package in the archive). Use the vip-manager utility to configure the IP address on the master server. In the vip-manager config, you need to configure the connection via DCS Consul. You also need to specify the consul_token, whose variable can be taken as consul.

The first thing we do is check the Vagrantfile and correct the data we need. Next, run Vagrantfile. After its completion, we launch consul.play.

vagrant up

#Start consul.play:

ansible-playbook consul.play

Open and edit hosts (inventory) so that ansible can manage our hosts. Open and edit ansible.cfg to specify our inventory file with all the parameters we need.

Create a folder (roles) where all playbooks and konifugrations for our clients will be stored. We create the handlers folder, and in it the playbook, which we will sometimes refer to - to restart postgresql. Create a tasks folder, and in it a playbook that pulls and downloads all the necessary packages: vip-manager, patroni. Specify the path where you need to install the configuration for postgresql and vip-manager. Run everything you need. Creating the templates folder, where the necessary configuration will be stored for postgresql - postgrsql.yml and for vip-manager - vip-manager.yml. Let's create a vars folder where all the variables that are used in many files will be stored and can change if necessary. Thus, we automate the whole process. In our case, we will have variable ports for listening and for connecting postgresql.

#Launching the playbook.yml, which specifies which hosts the folders belong to:

ansible-playbook playbook.yml

#We go to one of the clients, check our leader and replica:

watch patronictl list

# Changing our leader:

patronictl switchover

#We are watching and waiting for the leader to change:

watch patronictl list
