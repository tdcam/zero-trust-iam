# zero-trust-iam
How to configure Red Hat IdM for zero-trust identity management
-
I have included a couple of playbooks in this repo. 
-
The first one, 01-install-idm.yml, is just to install the packages
needed to run Red Hat Identity Manager. It installs the correct
packages and opens up the correct firewall ports.
-
The next one, 02-configure-idm.yml, does the actual installation.
Change the passwords, hostnames, ip addresses, reverse DNS zone,
and so on to your local settings.
-
03-register-clients.yml is the playbook to register Linux hosts
to your IdM server. Change the password, domain, hostname, etc.
to your local settings.
-
04-copy-ssh-configs.yaml is to distribute 01-idm-ssh.conf and
01-idm-sshd.conf to the machines which connect to your IdM server.
They configure ssh and sshd on your managed machines to set
GSSAPIAuthentication and GSSAPICleanupCredentials to "yes." 
This makes it so that your machines use the shared ssh keys on
systems which are registered to the IdM server instead of trying
to manage ssh keys with ssh-keygen and ssh-copy-id, which can be
a security risk.
-
ansible.cfg and inventory are just my local Ansible configuration 
files. I'm including them in the hopes that they're helpful.
-
Finally, beetles.txt, flintstones.txt, create-beetles.sh, and 
create-flintstones.sh are used to automate populating a bunch 
of bogus users for demo purposes. Should be pretty clear how
they work.
-
If you have any questions, email me at thomas@redhat.com.
