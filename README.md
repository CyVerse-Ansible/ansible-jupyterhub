ansible jupyterhub
==================

This role will install jupyterhub with CyVerse authentication and docker for jupyter notebooks.

Currently, Ubuntu 20 and 18 is tested and working.
It currently does not work properly on redhat systems, we are working on it.

Requirements
------------

This requires docker and k3s.

Role Variables
--------------

* AUTH_CLASS, can be set to github dummy or left blank witch will use pam authentication.
* DUMMY_PASS, a password for using dummy class. If not set dummy auth cannot be used.
* OAUTH2_CLIENT_ID, a client id for used for the following auths: github.
* OAUTH2_CLIENT_SECRET, a client secret for used for the following auths: github.
* OAUTH2_CALLBACK_URL, a callback url for used for the following auths: github.

Dependencies
------------

* Any role that installed docker ce and ansible_k3s form cyverse or any equivalent.

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
