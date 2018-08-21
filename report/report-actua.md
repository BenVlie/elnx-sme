# Enterprise Linux Lab Report

- Student name: Benjamin Van Lierde
- Github repo: <https://github.com/BenVlie/elnx-sme.git>

Describe the goals of the current iteration/assignment in a short sentence.
- Using a security tool to scan your system in order to secure it.
- Comparing potential dangers of servers that have different purposes.

## What is Lynis?

- https://cisofy.com/lynis/

#### TL:DR
A security auditing tool for linux that performs security scans very in depth and system-wide.

## Procedure/Documentation
- I install Lynis on Machines: pu001, pu004, pr001 and actua
- Actua is the clean install, this is the control.

- The things I will compare is the 'hardening index' * and the kind of warnings.
- Also possible suggestions given by the tool will be examined.

* Parameter that gives a number that symbols a impression of how hardened the system is, however it is not a percentage.


## Data

### control
![actuaControl1](https://github.com/BenVlie/elnx-sme/blob/master/report/images/actuaControlWarnings.png)

![actuaControl2](https://github.com/BenVlie/elnx-sme/blob/master/report/images/actuaControlIndex.png)


### pu001 (DNS master)
![pu001warnings](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pu001warnings.png)

![pu001index](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pu001Index.png)

### pu004 (LAMP)
![pu004warnings](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pu004warnings.png)


![pu004index](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pu004Index.png)

### pr001 (DHCP)
![pr001warnings](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pr001warnings.png)

![pr001index](https://github.com/BenVlie/elnx-sme/blob/master/report/images/pr001index.png)


## Results

### index
 The index is 67 or 68 for all tested machines. This makes sense because the machines all originate from the same box and the configurations have no focus on the security, except firewall.

### Nameservers
Because we configured our own DNS. The lynis tool does not recognize it. Every machine that uses the self-created DNS has the warning 'couldn't find responsive Nameservers'. Lynis tested the availability and if the DNS responds to queries. An easy fix would be: use external DNS.

Another DNS related issue occurs in the DNS server (pu001). The tool found the BIND version name in the banner. For security this should be hidden, an older version might have a unpatched breach and intruders can get the bind version easily.

The solution here is to set the version to 'none'.

### No GPG signing option.
This is a software flaw. The software repositories are not accessible via YUM.

### SMTP banner information leak
In this case, the banner includes the version number of the used software. This is easily spotted by an intruders recon attack.
Changing the banner in main.cf and restarting the daemon is a possible solution.

### vulnerable packages
In pu004 there are vulnerable packages, this is easily solved with the security plugin (yum-plugin-security).

### PHP - expose PHP
This warning says the expose PHP option might be enabled. This is another vulnerability for recon attacks as the version is easily spotted.
The easy fix is to disable expose PHP.

## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://cisofy.com/lynis/
- https://www.vultr.com/docs/how-to-install-and-use-lynis-on-centos-7
- https://cisofy.com/lynis/controls/NETW-2705/
- https://cisofy.com/lynis/controls/NAME-4210/
- https://cisofy.com/lynis/controls/PKGS-7387/
- https://cisofy.com/lynis/controls/MAIL-8818/
- https://cisofy.com/lynis/controls/PKGS-7386/
- https://cisofy.com/lynis/controls/PHP-2372/
