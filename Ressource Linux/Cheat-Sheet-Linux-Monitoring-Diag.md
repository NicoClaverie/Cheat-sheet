# Cheat Sheet Linux - Monitoring & Diagnostic (Debian / Ubuntu / Mint)

## 📊 Processus & CPU

| Catégorie     | Commande          | Description                                 |
| ------------- | ----------------- | ------------------------------------------- |
| Processus     | `top`             | Vue temps réel CPU/RAM/processus.           |
| Processus     | `htop`            | Version améliorée et colorée de `top`.      |
| Processus     | `atop`            | Analyse avancée + historique.               |
| Processus     | `ps aux`          | Liste tous les processus.                   |
| Processus     | `pidstat`         | Statistiques par processus (CPU, RAM, I/O). |
| CPU           | `mpstat -P ALL 1` | Charge par core en temps réel.              |
| CPU Profiling | `perf top`        | Profilage CPU (appels les plus coûteux).    |
| Multisystème  | `dstat`           | Combine vmstat / iostat / ifstat.           |

---

## 💾 Mémoire & Swap

| Catégorie | Commande            | Description                              |
| --------- | ------------------- | ---------------------------------------- |
| Mémoire   | `free -h`           | Utilisation de la RAM et swap (lisible). |
| Mémoire   | `vmstat 1`          | Statistiques mémoire et CPU.             |
| Mémoire   | `sar -r 1 3`        | Stats RAM via sysstat.                   |
| Mémoire   | `cat /proc/meminfo` | Infos détaillées sur la mémoire.         |

---

## ⚙️ Charge système

| Catégorie | Commande     | Description                      |
| --------- | ------------ | -------------------------------- |
| Charge    | `uptime`     | Charge moyenne + uptime.         |
| Charge    | `w`          | Charge + utilisateurs connectés. |
| Load      | `sar -q 1 3` | Analyse de la charge système.    |

---

## 💿 Disques / Storage / Filesystems

| Catégorie  | Commande               | Description                         |
| ---------- | ---------------------- | ----------------------------------- |
| Disques    | `df -h`                | Espace disque utilisé/total.        |
| Disques    | `du -sh /chemin`       | Taille d’un dossier.                |
| Disques    | `lsblk`                | Liste disques / partitions.         |
| Disques    | `blkid`                | UUID, type de partition.            |
| Disques    | `mount`                | Systèmes de fichiers montés.        |
| Storage    | `iostat -xz 1`         | I/O disque détaillées.              |
| Storage    | `smartctl -a /dev/sdX` | SMART disque (état matériel).       |
| Storage FS | `mount                 | column -t`                          | Liste lisible des montages. |
| Storage FS | `ncdu`                 | Explorateur CLI de l'espace disque. |

---

## 🧱 Systèmes de fichiers avancés

### Btrfs
| Commande                 | Description                |
| ------------------------ | -------------------------- |
| `btrfs subvolume list /` | Liste des sous-volumes.    |
| `btrfs filesystem df /`  | Espace utilisé/dédupliqué. |

### ZFS
| Commande       | Description     |
| -------------- | --------------- |
| `zpool status` | État des pools. |
| `zfs list`     | Volumes ZFS.    |

---

## 🌐 Réseau

| Catégorie | Commande                | Description                   |
| --------- | ----------------------- | ----------------------------- |
| Réseau    | `ip a`                  | Interfaces réseau.            |
| Réseau    | `ip r`                  | Table de routage.             |
| Réseau    | `ss -tulpn`             | Ports ouverts + processus.    |
| Réseau    | `ss -s`                 | Statistiques TCP.             |
| Réseau    | `ping 8.8.8.8`          | Test de connectivité.         |
| Réseau    | `dig domaine.com`       | Résolution DNS.               |
| Réseau    | `nslookup`              | DNS simplifié.                |
| Réseau    | `traceroute google.com` | Routage vers une destination. |

---

## 🌐 Analyse réseau avancée

| Commande          | Description                              |
| ----------------- | ---------------------------------------- |
| `mtr google.com`  | Traceroute + ping en continu.            |
| `iftop`           | Affiche la bande passante par interface. |
| `nethogs`         | Consommation réseau par processus.       |
| `tcpdump -i eth0` | Capture réseau brute.                    |
| `speedtest-cli`   | Test de débit internet.                  |

---

## 🔥 Services & Systemd

| Commande                      | Description               |
| ----------------------------- | ------------------------- |
| `systemctl status <service>`  | Statut d'un service.      |
| `systemctl restart <service>` | Redémarre un service.     |
| `systemctl enable <service>`  | Active au démarrage.      |
| `systemctl list-unit-files`   | Liste services installés. |
| `systemctl list-timers`       | Liste des timers.         |

---

## 📚 Logs & Audit

| Commande                  | Description                     |
| ------------------------- | ------------------------------- |
| `journalctl -xe`          | Logs système détaillés.         |
| `journalctl -f`           | Logs en direct.                 |
| `journalctl -u <service>` | Logs d'un service.              |
| `grep -r "mot" /var/log/` | Recherche dans les logs.        |
| `last`                    | Dernières connexions.           |
| `lastb`                   | Tentatives échouées.            |
| `faillog -a`              | Résumé des tentatives échouées. |

---

## 🎨 GPU

| Commande             | Description        |
| -------------------- | ------------------ |
| `lspci`              | grep -i vga`       | Identifier GPU. |
| `glxinfo`            | grep OpenGL`       | Infos OpenGL.   |
| `nvidia-smi`         | Monitoring NVIDIA. |
| `sudo intel_gpu_top` | Monitoring Intel.  |
| `sudo radeontop`     | Monitoring AMD.    |

---

## 🔥 Températures & Matériel

| Commande         | Description                 |
| ---------------- | --------------------------- |
| `sensors`        | Températures CPU/GPU.       |
| `sensors-detect` | Détecter les capteurs.      |
| `powertop`       | Analyse de la consommation. |
| `lshw -short`    | Matériel détaillé.          |
| `dmidecode`      | Infos BIOS / carte mère.    |

---

## 🐳 Docker / Conteneurs

| Commande                     | Description            |
| ---------------------------- | ---------------------- |
| `docker ps -a`               | Conteneurs présents.   |
| `docker stats`               | Monitoring conteneurs. |
| `docker logs -f <container>` | Logs en direct.        |
| `docker inspect <container>` | Infos détaillées.      |
| `docker system df`           | Espace disque utilisé. |

---

## 🧪 Tests & Stress

| Commande                         | Description       |
| -------------------------------- | ----------------- |
| `stress --cpu 4 --timeout 20`    | Charge CPU.       |
| `stress-ng --vm 1 --vm-bytes 1G` | Test mémoire.     |
| `fio --name=test --rw=readwrite` | Benchmark disque. |

---

## 🧭 Recherche & Navigation

| Commande                  | Description                  |
| ------------------------- | ---------------------------- |
| `find / -name fichier`    | Recherche fichier.           |
| `grep -R "texte" /chemin` | Recherche dans les fichiers. |
| `which commande`          | Localiser un binaire.        |

