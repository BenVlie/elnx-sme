# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

## Goals
- Setting up a samba file server and FTP server.
- Access control to files and directories.
- Using SELinux.
## Test plan

The first step is to destroy the current pu004 with ```vagrant destroy -f pr011``` and to reboot with ```vagrant up pr011```.
Secondly, log in with ```vagrant ssh pr011```.\
Now, go to the directory with the test script. ```cd /vagrant/test/``` and start the test ```sudo ./runbats.sh```
All tests should be successful.

## Procedure/Documentation4

The first step is working on the site.yml. I added the roles needed for the webserver there (rh-base,samba and vsftpd).
There is no error, the roles have been successfully installed.
The first thing I do is allowing services (samba and ftp) through the firewall. Secondly, I create user groups for samba to make use of. Next, I give a netbios name (files) and create a samba workgroup named 'avalon'. Furthermore, I disable printer sharing and anonoymous browsing and I Add a root /srv/shares/.

Next up is adding all users, including my own, from the employees file. Each user requires a name, comment, password and list of groups. Also samba requires seperate users with a name and password value.

As last, I implement the samba_shares.
All Samba tests are now successful, except read and write access for the public shares.

For vsftpd: I disabled anonymous users, set 'listen' to true, enabled local and set local root as /srv/samba_shares
The last step was setting up ACL's in the site.yml.


## Test report

![testrapport-03](https://github.com/BenVlie/elnx-sme/blob/master/report/images/03-testrapport.png)


## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://github.com/bertvv/ansible-role-rh-base
- https://github.com/bertvv/ansible-role-samba
- https://github.com/bertvv/ansible-role-vsftpd/
- https://docs.ansible.com/ansible/latest/modules/acl_module.html
