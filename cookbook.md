# Hacks and tricks
This is going to take some time to transcribe from cherry tree to here.....  

# Enumeration

## DNS (port 53)


### fierce dns
fierce -domain securitytrails.com

### nslookup
step: server 10.10.10.3
step: iptarget

### dig
dig axfr @10.10.10.13 cronos.htb

or with domain
dig @10.10.10.192 ForestDnsZones.BLACKFIELD.local

## Directory brute

  ### Gobuster
  
  -http dir search
  gobuster dir -w /usr/share/seclists/Discovery/Web-Content/raft-large-files.txt -u http://panda.htb.play -k -t 40
  
  
  -Subdomains search
  gobuster vhost -v -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -u http://workers.htb -o vhosts.txt
  
  
  

  
