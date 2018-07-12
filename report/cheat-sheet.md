# Cheat sheets and checklists

- Student name: Benjamin Van Lierde
- Github repo: Github.com/BenVLie/elnx-sme

## Basic commands

| Task                | Command |
| :---                | :---    |
| Query IP-adress(es) | `ip a`  |

## Git workflow

Simple workflow for a personal project without other contributors:

| Task                                         | Command                   |
| :---                                         | :---                      |
| Current project status                       | `git status`              |
| Select files to be committed                 | `git add FILE...`         |
| Commit changes to local repository           | `git commit -m 'MESSAGE'` |
| Push local changes to remote repository      | `git push`                |
| Pull changes from remote repository to local | `git pull`                |

## Checklist network configuration

1. Is the IP-adress correct? `ip a`
2. Is the router/default gateway correct? `ip r -n`
3. Is a DNS-server available? `cat /etc/resolv.conf`


## Troubleshooting Guide
- volg TCP/IP stack (beneden naar boven)
- link layer
- internet layer
- transport layer
- application layer
- know your network (weet welke waarden(ip adressen, poortnummers) je gaat krijgen)

### checklist link layer
   - test cables
   - check switch/NICs LEDs
   - ip link(=commando) (3) (Bij No carrier problemen met kabel)
   - in Vbox aansluiting adapters controleren (correct ip/subnet) (1)
   - check kabels aangesloten (2)

### checklist internet layer
   - Local settings
     - ip address: ip a (controleer ook subnets)
     - default gateway: ip r (verwacht 10.0.2.2 bij NAT)
     - DNS service: /etc/resolv.conf (Verwacht 10.0.2.3)
     - config files enp0s3 enp0s8 /etc/.../ (Als ip adres configuratie er is mag er geen DHCP zijn)
   - LAN connectivity
     - ping between hosts
     - ping default gateway/DNS
     - query DNS(dig, nslookup, getent) in syllabus troubleshooten DNS server, extra info
       - getent ahosts www.hogent.be
                 nslookup www.hogent.be // nslookup www.google.com (8.8.8.8) // dig www.hogent.be (+short)
                 reverse lookup : dig -x 178.62.144.90 (@193.190.173.1) (niet alle servers hebben reverse lookup)
                 getent = basistool // getent ahosts www.google.be
* SSH Check (sudo systemctl status ssh)
*           (sudo firewallcmd --list-all)
* SSH via Git Bash (ssh vagrant [IP] 192.168.56.42)

### checklist transport layer
   - service running? ->
      - sudo systemctl status "SERVICE": sudo systemctl start "service"
      - faalt? -> sudo journalctl -u (-f) xxxxx.Service
   - Correct port/interface -> sudo ss -tulpn (-n = poortnummers)
     - Verwachte poorten?
        - aanpassen in config file
      -> sudo systemctl restart xxxxx.service
   - firewallsettings
      - sudo firewall-cmd --list-all
      - sudo firewall-cmd --add-service=xxxxx
      - sudo firewall-cmd --add-service=xxxxx --permanent
      
### checklist application layer
   - check the logs: sudo journalctl -f -u "SERVICE"
   - check config file syntax
