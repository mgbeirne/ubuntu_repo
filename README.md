ubuntu_repo
=========

A role to build an local ubuntu mirror repository on a VM

Requirements
------------

Build a VM with about 2.5TB of disk space, but only allocate 20 GB for root and leave the rest unused.

After running the role, run the /var/spool/apt-mirror/sync_ubuntu_mirror.sh as user apt-mirror until it completes a full rsync, which may take days, so comment out the cron job in /etc/cron.d/apt-mirror until it is complete. On clients replace the Internet host in the file /etc/apt/sources.list with your local hostname and use it in any installs of new Ubuntu hosts.

Role Variables
--------------

Replace the password variable in tasks/main.yml with the output of ``"ansible-vault encrypt_string `openssl passwd -6 'MySuperSecretPassword'` --name "password"``
Then run the playbook as: "ansible-playbook --vault-id @prompt -i inventory main.yml" providing the password used to encrypt the above password.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles_path = ./roles
      become: true
      roles:
         - roles/ubuntu_repo

License
-------

GPL

Author Information
------------------

Mike Beirne http://home.xnet.com/~beirne/index.html
