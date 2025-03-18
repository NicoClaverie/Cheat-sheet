| #  | Commande         | Description                                                | Exemple d'utilisation                        |
|----|----------------|------------------------------------------------|--------------------------------|
| 1  | `ipconfig`      | Affiche les informations de configuration IP | `ipconfig /all` <br> `ipconfig /? ` |
| 2  | `systeminfo`    | Affiche les informations système | `systeminfo` |
| 3  | `netstat`       | Affiche les statistiques réseau | `netstat -ano` |
| 4  | `whoami`        | Affiche l'utilisateur actuel | `whoami` |
| 5  | `getmac`        | Affiche l'adresse MAC | `getmac /v` |
| 6  | `hostname`      | Affiche le nom de l'ordinateur | `hostname` |
| 7  | `ver`           | Affiche la version de Windows | `ver` |
| 8  | `winver`        | Affiche la version et la build de Windows | `winver` |
| 9  | `ping`          | Teste la connectivité réseau | `ping google.com` |
| 10 | `tracert`       | Trace la route vers une destination | `tracert microsoft.com` |
| 11 | `nslookup`      | Interroge les serveurs DNS | `nslookup google.com` |
| 12 | `tasklist`      | Liste les processus en cours d'exécution | `tasklist` |
| 13 | `taskkill`      | Termine un processus | `taskkill /IM notepad.exe /F` |
| 14 | `sfc`           | Analyse et répare les fichiers système | `sfc /scannow` |
| 15 | `chkdsk`        | Vérifie les erreurs sur un disque | `chkdsk C: /f` |
| 16 | `diskpart`      | Gère les disques et partitions | `diskpart` puis `list disk` |
| 17 | `format`        | Formate un disque | `format C: /fs:ntfs` |
| 18 | `xcopy`         | Copie des fichiers et répertoires | `xcopy C:\source D:\dest /E` |
| 19 | `robocopy`      | Outil avancé de copie de fichiers | `robocopy C:\source D:\dest /E` |
| 20 | `dir`           | Liste les fichiers et dossiers | `dir C:\` |
| 21 | `cd`            | Change de répertoire | `cd C:\Users` |
| 22 | `md`            | Crée un répertoire | `md NouveauDossier` |
| 23 | `rd`            | Supprime un répertoire | `rd AncienDossier` |
| 24 | `del`           | Supprime un fichier | `del C:\fichier.txt` |
| 25 | `copy`          | Copie un fichier | `copy C:\fichier.txt D:\` |
| 26 | `move`          | Déplace un fichier | `move C:\fichier.txt D:\` |
| 27 | `ren`           | Renomme un fichier ou un dossier | `ren ancien.txt nouveau.txt` |
| 28 | `type`          | Affiche le contenu d'un fichier texte | `type C:\fichier.txt` |
| 29 | `find`          | Recherche une chaîne dans un fichier | `find "erreur" C:\log.txt` |
| 30 | `findstr`       | Recherche des chaînes dans un fichier | `ipconfig /all | findstr DNS` |
| 31 | `sort`          | Trie le contenu d'un fichier | `sort < noms.txt` |
| 32 | `comp`          | Compare le contenu de deux fichiers | `comp fichier1.txt fichier2.txt` |
| 33 | `fc`            | Compare deux fichiers et affiche les différences | `fc fichier1.txt fichier2.txt` |
| 34 | `tree`          | Affiche l'arborescence des dossiers | `tree C:\` |
| 35 | `attrib`        | Modifie les attributs d'un fichier | `attrib +r C:\fichier.txt` |
| 36 | `cipher`        | Gère le chiffrement des fichiers | `cipher /e C:\SecretFolder` |
| 37 | `compact`       | Gère la compression des fichiers | `compact /c C:\dossier` |
| 38 | `powercfg`      | Gère les paramètres d'alimentation | `powercfg /energy` |
| 39 | `shutdown`      | Éteint ou redémarre l'ordinateur | `shutdown /r /t 0` |
| 40 | `gpupdate`      | Met à jour la stratégie de groupe | `gpupdate /force` |
| 41 | `gpresult`      | Affiche les résultats des stratégies de groupe | `gpresult /r` |
| 42 | `net user`      | Gère les comptes utilisateurs | `net user JohnDoe newpassword` |
| 43 | `net localgroup`| Gère les groupes locaux | `net localgroup Administrators` |
| 44 | `net start`     | Démarre un service | `net start "Print Spooler"` |
| 45 | `net stop`      | Arrête un service | `net stop "Print Spooler"` |
| 46 | `netsh`         | Outil de configuration réseau | `netsh wlan show profiles` |
| 47 | `sc`            | Gère les services Windows | `sc query` |
| 48 | `reg`           | Gère le registre Windows | `reg query HKLM\Software` |
| 49 | `runas`         | Exécute un programme en tant qu'autre utilisateur | `runas /user:Admin cmd` |
| 50 | `schtasks`      | Planifie l'exécution de tâches | `schtasks /create /tn "MaTache" /tr notepad.exe /sc daily` |
| 51 | `wmic`          | Outil avancé d'administration système | `wmic os get name,version,buildnumber` |
| 52 | `assoc`         | Affiche ou modifie les associations de fichiers | `assoc .txt` |
| 53 | `ftype`         | Affiche ou modifie les types de fichiers | `ftype txtfile` |
| 54 | `driverquery`   | Affiche les pilotes installés | `driverquery` |
| 55 | `msinfo32`      | Affiche les informations système | `msinfo32` |
| 56 | `mmc`           | Ouvre la console de gestion Microsoft | `mmc` |
| 57 | `eventvwr`      | Ouvre l'observateur d'événements | `eventvwr` |
| 58 | `services.msc`  | Ouvre la gestion des services | `services.msc` |
| 59 | `devmgmt.msc`   | Ouvre le gestionnaire de périphériques | `devmgmt.msc` |
| 60 | `diskmgmt.msc`  | Ouvre la gestion des disques | `diskmgmt.msc` |
| 61 | `taskmgr`       | Ouvre le gestionnaire des tâches | `taskmgr` |
| 62 | `perfmon`       | Ouvre le moniteur de performances | `perfmon` |
| 63 | `resmon`        | Ouvre le moniteur de ressources | `resmon` |
| 64 | `msconfig`      | Ouvre la configuration système | `msconfig` |
| 65 | `control`       | Ouvre le panneau de configuration | `control` |
| 66 | `mstsc`         | Ouvre la connexion bureau à distance | `mstsc` |
| 67 | `cleanmgr`      | Ouvre le nettoyage de disque | `cleanmgr` |
| 68 | `defrag`        | Défragmente un disque | `defrag C:` |
| 69 | `fsutil`        | Outil avancé du système de fichiers | `fsutil fsinfo drives` |
| 70 | `path`          | Affiche ou définit la variable PATH | `path` |
| 71 | `set`           | Affiche, modifie ou supprime des variables d'environnement | `set` |
| 72 | `echo`          | Affiche un message ou active/désactive l'écho | `echo Bonjour` |
| 73 | `cls`           | Efface l'écran | `cls` |
| 74 | `query`         | Affiche des informations sur les processus | `query process *` |
