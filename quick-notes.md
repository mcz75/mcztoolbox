# Workbench
Różne zapiski do używania, niesortowane.
## Dependency track

<https://github.com/pmckeown/dependency-track-maven-plugin#readme>

```shell 
mvn io.github.pmckeown:dependency-track-maven-plugin:upload-bom \
  -Ddependency-track.dependencyTrackBaseUrl=${DEPENDENCY_TRACK_BASE_URL} \
  -Ddependency-track.apiKey=${DEPENDENCY_TRACK_API_KEY}
```

### Add configuration for dependency-track and cyclonedx

https://cyclonedx.github.io/cyclonedx-maven-plugin/plugin-info.html
* cyclonedx:makeAggregateBom
* cyclonedx:makeBom
* cyclonedx:makePackageBom


https://github.com/pmckeown/dependency-track-maven-plugin#readme

``` pom.xml
<pluginManagement>
  <plugins>
    <plugin>
      <groupId>org.cyclonedx</groupId>
      <artifactId>cyclonedx-maven-plugin</artifactId>
      <version>2.7.9</version>
    </plugin>
    <plugin>
      <groupId>io.github.pmckeown</groupId>
      <artifactId>dependency-track-maven-plugin</artifactId>
      <configuration>
        <dependencyTrackBaseUrl>http://ppl-poz-pc0034:37011</dependencyTrackBaseUrl>
        <apiKey>THNVSAaR1y9Cl1HDkpfFrqtZiPXzI839</apiKey>
      </configuration>
    </plugin>
  </plugins>
</pluginManagement>
```

``` shell
mvn cyclonedx:makeBom
```
``` shell
mvn io.github.pmckeown:dependency-track-maven-plugin:upload-bom
```

## Linux

### Otwarte porty

```bash
# sprawdz czy konkretny port jest otwarty
netstat -na | grep :4000

# lista wszystkich otwartych portów
netstat -lntu
```

## Kali
From pluralsight 2023-10 [Kali Linux Concepts and Basic Functionality](https://app.pluralsight.com/course-player?clipId=05a10a92-c0e7-439b-b41a-b0b93d9488fd)

``` bash
# wolne miejsce
df -h

# wolna pamięć
free -m

# symulacja usunięcia pakietów (-s), autoremowe usuwa zalezne pakiety, samo remove tylko wybrany pakiet
sudo apt autoremove -s kali-tools-exploitation

# listowanie zainstalowanych pakietów
sudo apt list -i | grep kali-tools-

# aktualizacja

# aktualizacja informacji o pakietach
sudo apt update

# zaktualizowanie pakietów (full-upgrade usunie nieużywane pakiety)
sudo apt upgrade (or full-upgrade)

# instalacja pakietu z automatycznym potwierdzeniem
sudo apt -y install <package name>

#usunięcie pakietu i automatyczne potwierdzenie
sudo apt -y remove <package name>

# usunięcie nieużywanych pakietów
sudo apt autormemove
```

### Managing users

```bash
# add user
sudo adduser pluralsight

# change password for user
sudo passwd pluralsight

# change information about user
sudo chfn pluralsight

# change shell
sudo chsh pluralsight

# add user to a group
sudo adduser pluralsight2 --ingroup pluralsight

# add user to a sudo
sudo usermod -a -G sudo pluralsight2

# remove user account (leaves hoe and files)
sudo deluser pluralsight

# remove user with 
sudo deluser --remove-home --remove-all-files pluralsight2

# remove group
sudo delgroup pluralsight
```

### Managing services

```bash

# start service
sudo service nginx start
sudo service nginx stop
sudo service nginx restart #configuration changes
sudo service nginx status #not all services implement it

# to see available command
sudo service nginx

# status of all services
service --status-all

# enabling service to start automaticaly with os, then one need to start it manualy or reboot
sudo systemctl enable ssh
```

### xfce

Desktop Environment

<https://www.xfce.org/>

```shell
# print shell
echo $0 #/usr/bin/zsh

# see possible session managers ??? maybe I will understand it in the future
update-alternatives --config x-session-manager

#change session manager
sudo apt update
sudo apt install -y kali-desktop-gnome
update-alternatives --config x-session-manager

# to remove possible conflicting things
apt purge --autoremove kali-desktop-xfce
reboot

# install kali-linux on wsl
wsl --install --distribution kali-linux
# check
wsl -l -v

# check logs for user activity
sudo journalctl -a | grep COMMAND
```

* hd encyption
  * dm-crypt
* firewall:
  * ufw
  * Fail2ban
* internal scan
  * netstat
  * ss
* external scan
  * nmap
* review logs
  * snort
* Malware scanners
  * Chkrootkit
  * ClamAV
  * Lynis
  * Rkhunter
* Destroy files and subdirectories
  * shred
  * bleachbit
* some pages
  * <https://kali.org/>
  * <https://www.kali.org/docs/>
  * <https://www.kali.org/tools/all-tools/>
  * <https://offensive-security.com/>

### Vulnerable systems
* <https://www.vulnhub.com>
* <https://sourceforge.net/projects/metasploitable>

### DNS Analysis

#### DNSRecon
<https://www.kali.org/tools/dnsrecon/>

```shell
dnsrecon -h
```

#### DNSEnum
<https://www.kali.org/tools/dnsenum/>

 ```shell
dnsenum -h
 ```
#### DNSMap
Slowest, goes in subdomains
<https://www.kali.org/tools/dnsmap/>

### OSINT Analysis
Open Source inteligence gathering

#### Spiderfoot

<https://www.kali.org/tools/spiderfoot>

```shell
spiderfoot -l <ip:port> -s target -m modules to run against target -o output type
```
#### theHarvester

* <https://www.kali.org/tools/theharvester>
* <https://gitlab.com/kalilinux/packages/theharvester>

### Socian Engineering Attack

#### setoolkit

* <https://github.com/trustedsec/social-engineer-toolkit/raw/master/readme/User_Manual.pdf>

### Life host Identification
ARP scanning

#### Netdiscover

* <https://www.kali.org/tools/netdiscover/>

#### arp-scan

* <https://www.kali.org/tools/arp-scan/>

#### arp-fingerprint

### Network discovery

#### NMap

* <https://www.kali.org/tools/nmap/>
* <https://nmap.oeixrg>
* <https://nmap.org/book/toc>
* <https://nmap.org/docs.html>

Duże rozwiązanie, większe nisz samo Kali 
* NMAP Network Scanning
* NMAP Essentials
* Nmap 7: From Beginner to Pro

Virtualki do testowania
* <https://www.vulnhub.com/entry/mr-robot-1,151>
* <https://www.vulnhub.com/entry/metasploitable-2,29>

```shell
nmap -sV -p 21 192.168.1.53

#agressive scan
nmap -A 192.168.1.53

#execute scirpt
nmap -script ftp-vstpd-backdoor -p 21 192.168.1.53

#wcecute vuln scripts
nmap -script vuln -oX # <filename> <IP address>
nmap -script vuln -oX 53.xml 192.168.1.53

#this should generate 53.xml file
# convert it to html
xsltproc <xml filne name> -o <new html file name>
xsltproc 53.xml -o 53.html
```

## Keycloak

Wymaga javy potem sie rozpakowuje i uruchamia
 ``` shell
 $ bin/kc.sh start-dev
 ```

 ## Install on linux

 ### Check sum

 ```shell
 shasum plik 
 ```

 ## Git

 ### git svn

 <https://git-scm.com/docs/git-svn>

 ```shell
 git svn init -s 
 git svn clone -s
 ```

 ### Usunięcie referencji których nie ma zdalnie

 ```shell
 git remote prune origin
 ```

 
