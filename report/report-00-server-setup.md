# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

The first goal is to apply the role rhbase to the server pu004.
The second goal is to have a configuration for all hosts that:
  - Have EPEL repository installed
  - Have packages (bash-completion, bind-utils, git, nano, tree, vim-enhanced and wget) installed.
  - Create a administrator account.
  - Generate a ssh key pair.
  - Show the network connection after login.

## Test plan
The first step is to destroy the current pu004 with ```vagrant destroy -f pu004``` and to reboot with ```vagrant up pu004```.\
Secondly, log in with ```vagrant ssh pu004```.\
<<<<<<< HEAD
Now, go to the directory with the test script. ```cd /vagrant/test/``` and start the test ```sudo ./runbats.sh```
=======
Now, go to the directory with the test script. ```cd /vagrant/test/``` and start the test ```sudo ./runbats.sh``` \
>>>>>>> f2f532e781c3fc3fa317437c229ca5066052d089
All tests from common.bats should be successful.


## Procedure/Documentation

It was not difficult to do this part, because there was enough information in the syllabus and on github. One problem was puzzling around so the syntax was correct.
The hardest part was the ssh key pair. I had trouble locating the files on both host system and server.

## Test report

![testrapport-00](https://github.com/BenVlie/elnx-sme/blob/solution/images/00-testrapport.png)

## Resources
  - https://github.com/bertvv/ansible-role-rh-base
