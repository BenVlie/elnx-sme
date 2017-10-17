Slides: https://bertvv.github.io/presentation-el7-basics/
Extra broncode & testopstelling: https://github.com/bertvv/presentation-el7-basics
CheatSheet: https://github.com/bertvv/cheat-sheets/blob/master/src/EL7.md


Enterprise Linux 7 (RedHat, CentOS)
Commando's netwerkopstelling

Network settings:
'ip'
ip link
ip address (overzicht adressen)
ip a show dev (x*eml*x) (voor specifieke interface)
ip route routing info


VirtualBox ip adressen
 - NAT: IP = 10.0.2.15/24
 - GW = 10.0.2.2
 - DNS = 10.0.2.3
 - ip hostsysteem: Vbox -> file -> preferences -> network -> host-only networks -> hover opties
belangrijk voor troubleshooting: weten welke ip adressen
-op NAT interface altijd zelfde ip adres (10.0.0.15/24)
    -default gateway= 10.0.2.2/24
-bij vbox: file->preferences->network ->
    default HostOnly netwerk: host: 192.168.56.1/24
    DHCP server (simulated): 192.168.56.100
        geeft adressen range: 192.168.26.101- ".".".254
          *vagrant voegt automatisch goed host only toe*
alles moet kunnen pingen naar elkaar. (firewall afzetten?)
Vbox netwerken: NAT en host only adapters
DNS server opvragen: cat /etc/resolv.conf (10.0.2.3/24)
ip link toont interfaces vd datalink laag. (Ethernet)

TCP/IP lagen: werken van onder naar boven bij troubleshooting
-Applicatie: HTTP, DNS, DHCP
-transport: TCP/UDP, poorten
-internet: IP adresen, routering
-datalink: Ethernet, MAC adres
-fysiek

Interface names:
eml  -- EMbedded #
enol -- Ethernet Onboard adapter #
plpl -- PCI slot # poort #
enp0s3 -- Ethernet network Peripheral #serial#

cd /etc/sysconfig/network-scripts/ (toont config files van netwerken)
 *bij verandering, heropstarten met network.service*

Managing services (systemctl):
structuur: systemctl COMMAND [OPTION] ... name
List all services |systemctl --type=service
list running services | systemctl --state=running
list failed services | systemctl --failed
*systemctl enable httpd.service*
vb: systemctl status mariadb.service
  (opstarten) sudo systemctl (re)start mariadb.service

Show open sockets:
SS (was netstat)
Show server sockets | ss -l
show TCP/UDP sockets | ss -lt (TCP) ss -lu (UDP)
                * ss -ltn *
show port numbers(instead of service names from /etc/services) | ss -n
show process | ss -(lun)(ltn)p

firewall configuration
--firewalld--
List all zones* |firewall-cmd --get-zones
List active zone | firewall-cmd --get-active-zones
add interface to active zone |firewall-cmd --add-interface=interface
*zone = list of rules to be applied in a specific situation
  e.g. public(default), home, work*
*sudo systemctl start firewalld* start de firewall service

Task	                      Command
Show current rules	       | firewall-cmd --list-all
Allow predefined service	 | firewall-cmd --add-service=http
List predefined services	 | firewall-cmd --get-services
Allow specific port	       | firewall-cmd --add-port=8080/tcp
Reload rules	             | firewall-cmd --reload
Block all traffic	         | firewall-cmd --panic-on
Turn panic mode off	       | firewall-cmd --panic-off

Persistent changes
--permanent option => not applied immediately!
Two methods:
Execute command once without, once with  --permanent

poortnummer aanpassen: sudo vim /etc/httpd/conf/httpd.conf
                        sudo systemctl restart httpd
__Troubleshooting__
 - volg TCP/IP stack (beneden naar boven)
  -link layer
  -internet layer
  -transport layer
  -application layer
- know your network (weet welke waarden(ip adressen, poortnummers) je gaat krijgen)

-checklist link layer
    - test cables
    - check switch/NICs LEDs
    - ip link(=commando)
    - in Vbox aansluiting adapers controleren

-checklist internet layer
    - Local settings
      - ip address: ip a (controleer ook subnets)
      - default gateway: ip r
      - DNS service: /etc/resolv.conf
    - LAN connectivity
      - ping between hosts
      - ping default gateway/DNS
      - query DNS(dig, nslookup, getent) in syllabus troubleshooten DNS server, extra info
                  nslookup www.hogent.be // nslookup www.google.com (8.8.8.8) // dig www.hogent.be (+short)
                  reverse lookup : dig -x 178.62.144.90 (@193.190.173.1) (niet alle servers hebben reverse lookup)
                  getent = basistool // getent ahosts www.google.be

-checklist transport layer
    - service running? -> sudo systemctl status "SERVICE"
    - Correct port/interface -> sudo ss -tulpn (-n = poortnummers)
    - firewallsettings -> sudo firewall-cmd --list-all

-checklist application layer
    - check the logs: sudo journalctl -f -u "SERVICE"
    - check config file syntax