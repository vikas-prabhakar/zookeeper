To setup zookeeper cluster on aws via ansible.
Requirement: IP detail of Zookeeper Cluster
There are two ways to get the IP detail of Zookeeper cluster either static or get it through dynamic inventory by using a variable.
zookeeper_group is variable which will look for hosts from dynamic inventory.

We can add a machine dynamically into zookeeper cluster via exhibitor but in this repo, we can do it with Ansible too, by uncommenting rolling restart functionality and defining runtime variable rolling_restart

If you want to mount an additional partition for zookeeper then define ebs_vol and update the variable zookeeper_data_dir accordingly
e.g
ebs_vol:
  - partition: /dev/sdb
    mountpoint:/mnt

We have created a soft link to start/stop script along one update ${BASH_SOURCE-$0} with readlink $0
 
Notes: All the variables are defined in default/main.yml which are having low priority so you can overwrite it by defining either vars/main.yml or group_vars
