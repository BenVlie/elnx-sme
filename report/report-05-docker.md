# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

## Goals
- Setting up a webserver with databank in Docker and make it an automatic process in ansible.
## Test plan

- The first step is to destroy the current pr010 with ```vagrant destroy -f pr010``` and to reboot with ```vagrant up pr010```.\
Secondly, log in with ```vagrant ssh pu004```.\
- ```docker -v``` should show the version to ensure the installation is successful.
- Use ```sudo docker ps``` to see the containers.
- Use the given IP Adress ( In this case: 172.16.0.10)to browse to the website in the host system browser.


## Procedure/Documentation4
- First, I add the host pr010 with the box fedora 28 in vagrant-hosts.yml and do a first startup to download the box.
- vagrant plugin install vagrant-docker-compose
- Site.yml changed: Added role 'geerlingguy.docker'to host pr010.
- Used docker -v to check if docker is installed.
- Next, I create images in docker-compose.yml.
- Encountered problem: Python firewall.
  - I solved this by downgrading my OS from fedora 28 to 27.
- Encountered problem libselinux-python: The role rhbase gives an error around libselinux-python. I fixed this by removing the role and adding a pre-task that installs libselinux-python.
- After, I restarted the VM with destroy and up to see if it works completely in 1 run.


## Test report

### Show docker version and containers running on VM
![testrapport-05a](https://github.com/BenVlie/elnx-sme/blob/master/report/images/05a-testrapport.png)
\

### IP address in browser of host system and more screens.
![testrapport-05b](https://github.com/BenVlie/elnx-sme/blob/master/report/images/05b-testrapport.png)
\
![testrapport-05c](https://github.com/BenVlie/elnx-sme/blob/master/report/images/05c-testrapport.png)
\
![testrapport-05d](https://github.com/BenVlie/elnx-sme/blob/master/report/images/05d-testrapport.png)


## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://galaxy.ansible.com/geerlingguy/docker
- https://ansible.github.io/ansible-container-demo/
- http://docs.ansible.com/ansible-container/getting_started.html
- https://github.com/ansible/ansible-container
- http://docs.ansible.com/ansible/latest/guide_docker.html
- http://docs.ansible.com/ansible/latest/list_of_cloud_modules.html#docker  
- https://galaxy.ansible.com/geerlingguy/docker
- https://docs.docker.com/compose/compose-file/
- https://hub.docker.com/_/wordpress/>
- https://hub.docker.com/_/mysql/
- https://www.youtube.com/watch?v=Qw9zlE3t8Ko
