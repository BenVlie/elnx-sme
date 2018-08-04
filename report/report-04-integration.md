# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme>

- Setting up a DHCP server.
- Setting up a router with VyOS.

## Test plan
- Make a new virtual machine with Fedora or Ubuntu.
- Change the network adaptors of this machine to: 2 host-only adaptors with IP: 172.16.0.0 SM: 255.255.0.0
- Write down the MAC address of 1 adaptor in the ansible configuration and provision the server.
- With the use of ip a check the IP addresses. The IP address should be in the range of the DHCP configuration.


## Procedure/Documentation

### DHCP server
- Added pr001 to site.yml.
- Create and configure pr001.yml
  - Allow dhcp trough firewall.
  - Added configurations for lease time, subnet mask, router and domain name.
  - Added subnet.
  - Added host.

### router
- Installed the vyos plugin.
- Configured the router in the shell script:
  - basic settings.
  - IP settings
  - NAT
  - time
  - DNS

## Test report

![testrapport-04a](https://github.com/BenVlie/elnx-sme/blob/solution/images/04a-testrapport.png)

![testrapport-04b](https://github.com/BenVlie/elnx-sme/blob/solution/images/04b-testrapport.png)

## Resources
  - https://github.com/bertvv/ansible-role-rh-base
