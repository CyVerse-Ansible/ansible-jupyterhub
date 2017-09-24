ansible jupyterhub
==================

This role will install jupyterhub with CyVerse authentication and docker for jupyter notebooks.

Currently, Ubuntu 16 is supported. CentOS 7 will be supported shortly.

CentOS 6 is not supported

Requirements
------------

This requires docker

Role Variables
--------------

* jupyterhub_system_config, the directory containing the jupyter configuration (default: /etc/jupyterhub)
* jupyterhub_log, the path to the jupyterhub log file (default: /var/log/jupyterhub.log)
* jupyterhub_dockerhost_ip, the default internal ip of the docker host (default: 172.17.0.1)
* jupyterhub_docker_image, the default docker image to use for jupyter notebooks (default: jupyter/datascience-notebook)
* jupyterhub_config_admin_users, the set of users with admin rights (default: "set()" or empty)
* jupyterhub_systemd_after, setting used for the systemd config file. Note, this is distro specific.
* jupyterhub_mod_auth_cas_config_path, location of the apache module configuration path

Dependencies
------------

* Any role that installed docker ce

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- name: This playbook will install jupyterhub
  hosts: jupyterhub
  roles:
  - ansible-docker
  - jupyterhub 

License
-------

BSD

Author Information
------------------

For more information, please contact Edwin Skidmore (edwin@cyverse.org)
