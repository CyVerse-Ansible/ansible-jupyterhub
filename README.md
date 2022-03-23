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
* JH_SINGLEUSER_IMAGE, the image to use for jupyter; default is jupyter/datascience-notebook
* JH_SINGLEUSER_IMAGE_TAG, the image tag to use for jupyter; default is latest
* JH_SINGLEUSER_DEFAULT_URL, the default url for jupyter; default is "/lab"

* JH_ALLOWED_USERS, list of users allowed to login to app
* JH_ADMINS, list of admin users

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
