# Nmap Switch Options

## Target Specification

| SWITCH      | EXAMPLE                   | DESCRIPTION                         |
|-------------|---------------------------|-------------------------------------|
| (none)      | `nmap 192.168.1.1`        | Scan a single IP                    |
| (none)      | `nmap 192.168.1.1 192.168.2.1` | Scan specific IPs               |
| (none)      | `nmap 192.168.1.1-254`    | Scan a range                        |
| (none)      | `nmap scanme.nmap.org`    | Scan a domain                       |
| (none)      | `nmap 192.168.1.0/24`     | Scan using CIDR notation            |
| `-iL`       | `nmap -iL targets.txt`    | Scan targets from a file            |
| `-iR`       | `nmap -iR 100`            | Scan 100 random hosts               |
| `-exclude`  | `nmap -exclude 192.168.1.1` | Exclude listed hosts              |

---

## Port Specification

| SWITCH              | EXAMPLE                              | DESCRIPTION                                                                 |
|---------------------|--------------------------------------|-----------------------------------------------------------------------------|
| `-p`                | `nmap 192.168.1.1 -p 21`             | Port scan for port x                                                        |
| `-p`                | `nmap 192.168.1.1 -p 21-100`         | Port range                                                                  |
| `-p`                | `nmap 192.168.1.1 -p U:53,T:21-25,80`| Port scan multiple TCP and UDP ports                                         |
| `-p`                | `nmap 192.168.1.1 -p-`               | Port scan all ports                                                         |
| `-p`                | `nmap 192.168.1.1 -p http,https`     | Port scan from service name                                                 |
| `-F`                | `nmap 192.168.1.1 -F`                | Fast port scan (100 ports)                                                  |
| `-top-ports`        | `nmap 192.168.1.1 --top-ports 2000`  | Port scan the top x ports                                                   |
| `-p-65535`          | `nmap 192.168.1.1 -p-65535`          | Leaving off end port in range makes the scan start at port 1                |
| `-p0-`              | `nmap 192.168.1.1 -p0-`              | Leaving off end port in range makes the scan go through to port 65535       |

---

## Service and Version Detection

| SWITCH                    | EXAMPLE                                         | DESCRIPTION                                                                     |
|---------------------------|-------------------------------------------------|---------------------------------------------------------------------------------|
| `-sV`                     | `nmap 192.168.1.1 -sV`                          | Attempts to determine the version of the service running on port                |
| `-sV --version-intensity`  | `nmap 192.168.1.1 -sV --version-intensity 8`    | Intensity level 0 to 9. Higher number increases possibility of correctness      |
| `-sV --version-light`      | `nmap 192.168.1.1 -sV --version-light`          | Enable light mode. Lower possibility of correctness. Faster                     |
| `-sV --version-all`        | `nmap 192.168.1.1 -sV --version-all`            | Enable intensity level 9. Higher possibility of correctness. Slower             |
| `-A`                      | `nmap 192.168.1.1 -A`                           | Enables OS detection, version detection, script scanning, and traceroute        |

---

## Host Discovery

| SWITCH         | EXAMPLE                                     | DESCRIPTION                                                         |
|----------------|---------------------------------------------|---------------------------------------------------------------------|
| `-sL`          | `nmap 192.168.1.1-3 -sL`                    | No Scan. List targets only                                           |
| `-sn`          | `nmap 192.168.1.1/24 -sn`                   | Disable port scanning. Host discovery only                           |
| `-Pn`          | `nmap 192.168.1.1-5 -Pn`                    | Disable host discovery. Port scan only                               |
| `-PS`          | `nmap 192.168.1.1-5 -PS22-25,80`            | TCP SYN discovery on port x. Port 80 by default                      |
| `-PA`          | `nmap 192.168.1.1-5 -PA22-25,80`            | TCP ACK discovery on port x. Port 80 by default                      |
| `-PU`          | `nmap 192.168.1.1-5 -PU53`                  | UDP discovery on port x. Port 40125 by default                       |
| `-PR`          | `nmap 192.168.1.1/24 -PR`                   | ARP discovery on local network                                       |
| `-n`           | `nmap 192.168.1.1 -n`                       | Never do DNS resolution                                              |

---

## NSE Scripts

| SWITCH            | EXAMPLE                                                    | DESCRIPTION                                                                 |
|-------------------|------------------------------------------------------------|-----------------------------------------------------------------------------|
| `-sC`             | `nmap 192.168.1.1 -sC`                                     | Scan with default NSE scripts. Considered useful for discovery and safe     |
| `-script default` | `nmap 192.168.1.1 --script default`                        | Scan with default NSE scripts. Considered useful for discovery and safe     |
| `-script`         | `nmap 192.168.1.1 --script=banner`                         | Scan with a single script. Example banner                                   |
| `-script`         | `nmap 192.168.1.1 --script=http*`                          | Scan with a wildcard. Example http                                          |
| `-script`         | `nmap 192.168.1.1 --script http,banner`                    | Scan with two scripts. Example http and banner                              |
| `-script`         | `nmap 192.168.1.1 --script "not intrusive"`                | Scan default, but remove intrusive scripts                                  |
| `-script-args`    | `nmap --script snmp-sysdescr --script-args snmpcommunity=admin 192.168.1.1` | NSE script with arguments                                                  |

---

## OS Detection

| SWITCH                | EXAMPLE                                        | DESCRIPTION                                                                 |
|-----------------------|------------------------------------------------|-----------------------------------------------------------------------------|
| `-O`                  | `nmap 192.168.1.1 -O`                          | Remote OS detection using TCP/IP stack fingerprinting                       |
| `-O --osscan-limit`   | `nmap 192.168.1.1 -O --osscan-limit`           | If at least one open and one closed TCP port are not found it will not try OS detection against host |
| `-O --osscan-guess`   | `nmap 192.168.1.1 -O --osscan-guess`           | Makes Nmap guess more aggressively                                          |
| `-O --max-os-tries`   | `nmap 192.168.1.1 -O --max-os-tries 1`         | Set the maximum number x of OS detection tries against a target             |
| `-A`                  | `nmap 192.168.1.1 -A`                          | Enables OS detection, version detection, script scanning, and traceroute    |
