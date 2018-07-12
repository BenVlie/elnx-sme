# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

Setting up a master and slave DNS server with BIND.
## Test plan

The first step is to destroy the current servers with ```vagrant destroy -f pu001```, ```vagrant destroy -f pu002``` and to reboot with ```vagrant up pu001, 002```.\
Secondly, log in with ```vagrant ssh pu001,002```.\
Now, go to the directory with the test script. ```cd /vagrant/test/``` and start the test ```sudo ./runbats.sh``` \
Respectively, the test for masterdns.bats and slavedns.bats should be successful

## Procedure/Documentation4

- The first step is working on the site.yml. I added the role needed for the DNS servers there (bind).
- The first thing I do is allowing DNS service through the firewall for the master and slave server.
#### Master DNS server
- I looked up the information needed for the BIND configurations. Starting with the master server. I add  The zone name, master server ip, zone networks and zone name servers to pu001.\ After, I add all zone hosts with their ip addresses and an alias. Furthermore I make sure it listens to ipv4 and give it permission to query.
- Finally, I added a MX record.

#### Slave dns
- I copy the same general settings from the Master dns.


## Test report
### Acceptance Tests
![testrapport-02a](https://github.com/BenVlie/elnx-sme/blob/master/report/images/02a-testrapport.png)
![testrapport-02b](https://github.com/BenVlie/elnx-sme/blob/master/report/images/02b-testrapport.png)

## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://github.com/bertvv/ansible-role-rh-base
- https://github.com/bertvv/ansible-role-bind
