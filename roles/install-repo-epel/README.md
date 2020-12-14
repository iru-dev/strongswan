install-repo-Epel
=========

Роль устанавливает репозиторий Epel

Requirements
------------

###

Role Variables
--------------
epel_repo_url: "https://dl.fedoraproject.org/pub/epel/epel-release-latest-{{ ansible_distribution_major_version }}.noarch.rpm"
epel_repo_gpg_key_url: "/etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-{{ ansible_distribution_major_version }}"
epel_repofile_path: "/etc/yum.repos.d/epel.repo"

Dependencies
------------

###

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- hosts: localhost
  strategy: free
  vars:
    - just_installed: true

  roles:
    - install-repo-Epel

License
-------

BSD

Author Information
------------------
check meta
