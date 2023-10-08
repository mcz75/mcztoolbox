# Workbench
Różne zapiski do używania, niesortowane.
## Dependency track

<https://github.com/pmckeown/dependency-track-maven-plugin#readme>

mvn io.github.pmckeown:dependency-track-maven-plugin:upload-bom \
  -Ddependency-track.dependencyTrackBaseUrl=${DEPENDENCY_TRACK_BASE_URL} \
  -Ddependency-track.apiKey=${DEPENDENCY_TRACK_API_KEY}

### Add configuration for dependency-track

https://cyclonedx.github.io/cyclonedx-maven-plugin/plugin-info.html
cyclonedx:makeAggregateBom
cyclonedx:makeBom
cyclonedx:makePackageBom

``` cmd
mvn cyclonedx:makeBom
```

https://github.com/pmckeown/dependency-track-maven-plugin#readme

``` cmd
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
From pluralsight 2023-10

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