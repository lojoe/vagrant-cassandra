# vagrant-cassandra

A Vagrant and Ansible powered mini Apache Cassandra cluster for R&amp;D.

# Prerequisites

- A working Vagrant installation using the Parallels provider
- A working Ansible installation
- A recent Oracle JRE 7 or 8 RPM (http://www.oracle.com/technetwork/java/javase/downloads/index.html)

# Installation

```bash
git clone https://github.com/lojoe/vagrant-cassandra.git
cd vagrant-cassandra
# Copy your Java RPM into ansible/roles/java/files
# Update ansible/cassandra.yml variable java_rpm
# Adjust Vagrantfile for your environment
vagrant up
```
