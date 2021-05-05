Docker-Portainer-Agent
=========

This role installs the portainer agent container on a docker host. This allows the host to be managed by my portainer instance. 

Requirements
------------

Docker needs to be installed and configured on the server. 

Role Variables
--------------

Required variables are listed here, along with default example values. See defaults/main.yml. Any of these defaults can be overwritten by using the vars role directory. 

    container_name: portainer_agent

This is the name of the container.

The image container. By default this pulls from the portainer docker repository.

    container_ports:
     - 9001:9001

These are the exported ports of the container.

    docker_socket_directory: /var/run/docker.sock

This is the location of the docker socket file.

    docker_socket_directory: /var/run/docker.sock

This is the directory that of docker volumes. This was taken from the install instructions.

    agent_environment_variables:
      PUID: "1000"
      PGID: "1000"
      TZ: America/Chicago

These are additional environmental variables for the container.

    agent_docker_additional_options:
      restart_policy: always

A dictionary of additional container properties. By default this just sets the container to always restart.

Dependencies
------------

None.

Example Playbook
----------------

    - name: Deploy the Portainer_Agent container.
      hosts: docker
      become: true
      roles:
        - role: docker-portainer-agent

This playbook deploys the portainer_agent container on all of my docker hosts.

License
-------

BSD

Author Information
------------------

Derek Smiley - Aspiring System Administrator/Ansible Automation Engineer

Connect with me on LinkedIn - https://www.linkedin.com/in/derek-smiley/