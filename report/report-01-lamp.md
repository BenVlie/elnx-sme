# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

Setting up a webserver with Apache, MariaDB and Wordpress.
## Test plan

The first step is to destroy the current pu004 with ```vagrant destroy -f pu004``` and to reboot with ```vagrant up pu004```.\
Secondly, log in with ```vagrant ssh pu004```.\
Now, go to the directory with the test script. ```cd /vagrant/test/``` and start the test ```sudo ./runbats.sh```
All lamp.bats tests should be successful.

## Procedure/Documentation4

The first step is working on the site.yml. I added the roles needed for the webserver there (mariadb, httpd and wordpress). Using provision to see if there's an error.
There is no error, the roles have been successfully installed. Next, I check if any acceptance tests have been succesful.
After reading the github page (rhbase and mariadb). The first thing I do is allowing services (http, https) through the firewall. Secondly, I create a DB for Wordpress. Also, I added myself as user with wordpress access. Added a root password and the variable php for httpd scripting. Added wordpress db, user and password.\
For the certificates I did research. Even with the information it took some trial and error to get a correct result in the acceptance tests.

## Test report

![testrapport-01](https://github.com/BenVlie/elnx-sme/blob/master/report/images/01-testrapport.png)
The test report is a transcript of the execution of the test plan, with the actual results. Significant problems you encountered should also be mentioned here, as well as any solutions you found. The test report should clearly prove that you have met the requirements.

## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://github.com/bertvv/ansible-role-mariadb
- https://github.com/bertvv/ansible-role-httpd
- https://github.com/bertvv/ansible-role-rh-base
- https://github.com/bertvv/ansible-role-wordpress
- https://blog.confirm.ch/deploying-ssl-private-keys-with-ansible/
- https://blog.red-badger.com/blog/2014/02/28/deploying-ssl-keys-securely-with-ansible
- https://github.com/openmicroscopy/ansible-role-ssl-certificate
