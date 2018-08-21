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

- * Parameter that gives a numer that symbols a impression of how hardened the system is, however it is not a percentage.


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

## Resources

List all sources of useful information that you encountered while completing this assignment: books, manuals, HOWTO's, blog posts, etc.
- https://cisofy.com/lynis/
- https://www.vultr.com/docs/how-to-install-and-use-lynis-on-centos-7
