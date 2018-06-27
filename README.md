ansible-influxdb-in-docker
=========
:shipit: Ansible galaxy role to deploy [InfluxDB](https://www.influxdata.com/) in docker

The purpose of this Ansible role is to allow you to manage a
[InfluxDB](https://www.influxdata.com/) time series database.

With this role you will be able to deploy a [InfluxDB](https://www.influxdata.com/) container on you server.


Requirements
------------

The following packages have to be installed and well configured on the host :
- [Docker-ce](https://docs.docker.com/engine/installation/)

Role Variables
--------------

### User defined variables
The following vars have to be defined on each execution by the user to configure the InfluxDB configuration

#### Mandatory - Endpoints list configuration

### Overridable default variables
#### Name of the InfluxDB docker container
```yaml
influxdb_container_name: "influxdb"
```

#### Path on the host filesystem where will be the InfluxDB conf and data files
```yaml
influxdb_root_location: "/opt/docker-data/{{ influxdb_container_name }}"
influxdb_conf_location: "{{ influxdb_root_location }}/conf"
influxdb_data_location: "{{ influxdb_root_location }}/data"
```

#### Docker networks
```yaml
influxdb_docker_networks: []
#influxdb_docker_networks:
#  - name: "docker_network"
```

#### Docker container restart policy
```yaml
influxdb_container_restart_policy: "always" #(always, no, on-failure, unless-stopped)
```

Dependencies
------------

--

Example Playbook
----------------

See tests/test.yml  
  * `ansible-playbook tests/test.yml --ask-sudo-password -e influxdb_root_location="$(pwd)/.workdir/"`
  * On MacsOS due to Docker Machine root limitation : add `-e ansible_become_user="$(whoami)"`
```yaml
- hosts: localhost
  roles:
    - role: ../ansible-influxdb-in-docker
```
License
-------

MIT

Author Information
------------------

https://github.com/BastienF/ansible-influxdb-in-docker
