# Ansible Hadoop Core

This is a Ansible role to install Apache Hadoop Core (support ubuntu16.04/centos7)

## Requirements

Ansible 2.1

## Role Variables

|Variable|Default Value|Description|
|---|---|---|
```hadoop_version```|2.7.4|hadoop-core version.
```hadoop_user```|hduser|hadoop user account.
```java_home```|/usr/lib/jvm/java-8-openjdk-amd64|java home environment variable
```hadoop_home```|/usr/local/hadoop|hadoop home environment variable.
```hadoop_conf_dir```|/etc/hadoop|hadoop conf path environment variable.
```hadoop_log_dir```|/var/log/hadoop|hadoop log path environment variable.
```hadoop_pid_dir```|/var/run/hadoop|hadoop pid path environment variable.
```hadoop_namenode```|127.0.0.1|hdfs namenode address.
```hadoop_namenode_prot```|8020|hdfs namenode port.
```hadoop_secondarynamenode```|127.0.0.1|secondarynamenode address.
```hadoop_secondarynamenode_port```|50090|secondarynamenode port.
```mapreduce_framework_name```|yarn|mapreduce framework name.
```yarn_resourcemanager_hostname```|127.0.0.1| yarn resourcemanager hostname.
```hadoop_slaves```|['127.0.0.1']|hadoop slave address list.

## Example
```
### create a requirements.yml
- src: git+https://github.com/willyhutw/ansible-role-hadoop-core.git
  name: ansible-role-hadoop-core

### create a playbook.yml
- hosts: all
  become: yes
  roles:
    - roles/ansible-role-hadoop-core

### install this role
ansible-galaxy install -r requirements.yml -p ./roles

### run it!
ansible-playbook -i '192.168.33.151, 192.168.33.152, 192.168.33.153,' playbook.yml \
-e "ansible_ssh_user=vagrant ansible_ssh_pass=vagrant" \
-e "hadoop_namenode=192.168.33.151" \
-e "hadoop_secondarynamenode=192.168.33.152" \
-e "yarn_resourcemanager_hostname=192.168.33.151" \
-e "{'hadoop_slaves':['192.168.33.151','192.168.33.152','192.168.33.153']}"
```

## License

MIT / BSD

## Author Information

willyhu.tw@gmail.com

