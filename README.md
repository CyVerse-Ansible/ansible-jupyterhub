ansible jupyterhub
==================

This role will install zero-to-jupyterhub.

Currently, Ubuntu 20 and 18 is tested and working.
It currently does not work properly on redhat systems, we are working on it.

Requirements
------------

This requires docker and k3s.

Role Variables
--------------

* JH_AUTH_CLASS, can be set to `github`, `dummy` or left blank witch will use pam authentication.
* JH_DUMMY_PASS, a password for using dummy class. If not set dummy auth cannot be used.
* JH_OAUTH2_CLIENT_ID, a client id for used for the following auths: github.
* JH_OAUTH2_CLIENT_SECRET, a client secret for used for the following auths: github.
* JH_OAUTH2_CALLBACK_URL, a callback url for used for the following auths: github.
* JH_SINGLEUSER_EXCLUDE_MASTER, if true will prevent single user notebooks from running on master node

* JH_SINGLEUSER_IMAGE, the image to use for jupyter; default is jupyter/datascience-notebook
* JH_SINGLEUSER_IMAGE_TAG, the image tag to use for jupyter; default is latest
* JH_SINGLEUSER_DEFAULT_URL, the default url for jupyter; default is "/lab"
* JH_SINGLEUSER_GPU_ENABLE, default is no gpu
* JH_SINGLEUSER_START_TIMEOUT, timeout setting to wait for the single user containers to start; default is 600
* JH_SINGLEUSER_HTTP_TIMEOUT, timeout setting to wait for the single user container-to-hub communication; default 600
* JH_SINGLEUSER_MEMORY_GUARANTEE, minimum memory to set for single user containers; default 1G
* JH_SINGLEUSER_MEMORY_LIMIT, max memory to set for single user containers; no default (unlimited)
* JH_SINGLEUSER_CPU_GUARANTEE, minimum cpu to set for single user containers; default 0.5
* JH_SINGLEUSER_CPU_LIMIT, max cpu to set for single user containers; no default (1 cpu?)

* JH_ALLOWED_USERS, list of users allowed to login to app
* JH_ADMINS, list of admin users

* JH_SHARED_STORAGE_ENABLE, set to true if enabling storage
* JH_SHARED_STORAGE_PV_NAME, set to the persistent volume name
* JH_SHARED_STORAGE_PVC_NAME, set to the persistent volume claim name
* JH_SHARED_STORAGE_MOUNT_DIR, set to the mount directory within container, default = /home/jovyan/shared

* JH_RESOURCES_REQUEST_CPU, if set this is the cpu setting for the hub container, 0m - 1000m
* JH_RESOURCES_REQUEST_MEMORY, if set this is the memory setting for the hub container, 200Mi - 4Gi

* JH_INGRESS_ENABLED, if set this will enable ingress
* JH_INGRESS_CLASS, default is `nginx`
* JH_INGRESS_BODY_SIZE, will set the maximum proxy body size. Default is "4096m"
* JH_INGRESS_HOSTNAME, if set will set the hostname for ingress

* JH_DB_PVC_STORAGE_CLASS_NAME, if set will be the storageclass name

* JH_PREPULL_IMAGES, if set the hub will prepull images to all nodes before its available. Set to false if the images are too large or too many nodes. default is true.

Dependencies
------------

* This role requires kubernetes, generally is installed with k3s. If helm is not installed, then it will install it.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- name: This playbook will install jupyterhub
  hosts: jupyterhub
  roles:
  - ansible-docker
  - ansible-jupyterhub

License
-------

BSD

Author Information
------------------

For more information, please contact Edwin Skidmore (edwin@cyverse.org)
