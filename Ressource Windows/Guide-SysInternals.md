# Suite Microsoft Sysinternals

**Résumé** : La suite Sysinternals est un ensemble de plus de 70 utilitaires de dépannage et de gestion système avancés pour la plateforme Windows. Initialement créés par Mark Russinovich et Bryce Cogswell (Winternals), ces outils sont devenus la référence absolue pour les administrateurs système, les développeurs et les experts en cybersécurité. Ils permettent d'explorer les entrailles de l'OS, de diagnostiquer des pannes complexes et de détecter des activités suspectes qu'aucun outil standard de Windows ne peut voir.

**Exemple d'utilisation globale** Imaginons un ordinateur qui ralentit sans raison apparente :

1. Vous utilisez **Process Explorer** pour identifier un processus gourmand.

2. Vous lancez **Process Monitor** pour voir quel fichier ce processus essaie de lire en boucle.

3. Vous vérifiez avec **Autoruns** comment ce processus s'est programmé pour démarrer automatiquement.

#### Liens Utiles
Documentation officielle : [Portail Microsoft Learn Sysinternals](https://learn.microsoft.com/fr-fr/sysinternals/)

Téléchargement de la suite complète : [SysinternalsSuite.zip](https://download.sysinternals.com/files/SysinternalsSuite.zip)

Accès direct (Live) : 
Accessible via l'explorateur de fichier ou Win+R
```
\\live.sysinternals.com\tools
```

#### Installation via Winget
Pour installer l'intégralité de la suite d'un seul coup sur votre machine :
```
winget install Microsoft.Sysinternals
```

### Catégories principales
Les outils sont généralement classés en 6 familles :

[Utilitaires de fichiers et de disques](https://learn.microsoft.com/fr-fr/sysinternals/downloads/file-and-disk-utilities) (AccessChk, Diskmon...)

[Utilitaires de mise en réseau](https://learn.microsoft.com/fr-fr/sysinternals/downloads/networking-utilities) (TCPView, AdExplorer...)

[Utilitaires de processus](https://learn.microsoft.com/fr-fr/sysinternals/downloads/process-utilities) (Process Explorer, ProcMon...)

[Utilitaires de sécurité](https://learn.microsoft.com/fr-fr/sysinternals/downloads/security-utilities) (Autoruns, Sigcheck...)

[Utilitaires d’informations système](https://learn.microsoft.com/fr-fr/sysinternals/downloads/system-information) (BgInfo, Coreinfo...)

[Utilitaires divers](https://learn.microsoft.com/fr-fr/sysinternals/downloads/misc-utilities)  (ZoomIt, Desktops...)



## Sommaires

1. [Utilitaires de fichiers et de disques](#utilitaires-de-fichiers-et-de-disques)
   - [AccessChk](#accesschk)
   - [AccessEnum](#accessenum)
   - [CacheSet](#cacheset)
   - [Contig](#contig)
   - [Disk2vhd](#disk2vhd)
   - [DiskExt](#diskext)
   - [DiskMon](#diskmon)
   - [DU (Disk Usage)](#du-disk-usage)
   - [DiskView](#diskview)
   - [EFSDump](#efsdump)
   - [jcd](#jcd)
   - [LDMDump](#ldmdump)
   - [NTFSInfo](#ntfsinfo)
   - [PendMoves et MoveFile](#pendmoves-et-movefile)
   - [RegMon](#regmon)
   - [SDelete](#sdelete)
   - [Sigcheck](#sigcheck)
   - [Streams](#streams)
   - [Sync](#sync)
   - [VolumeID](#volumeid)

2. [Utilitaires de mise en réseau](#utilitaires-de-mise-en-réseau)
   - [AD Explorer](#ad-explorer)
   - [ADInsight](#adinsight)
   - [ADRestore](#adrestore)
   - [PipeList](#pipelist)
   - [PsFile](#psfile)
   - [PsPing](#psping)
   - [ShareEnum](#shareenum)
   - [TCPView](#tcpview)
   - [Whois](#whois)

3. [Utilitaires de processus](#utilitaires-de-processus)
   - [Autoruns](#autoruns)
   - [Handle](#handle)
   - [ListDLLs](#listdlls)
   - [Portmon](#portmon)
   - [ProcDump](#procdump)
   - [Process Explorer](#process-explorer)
   - [Process Monitor](#process-monitor)
   - [PsExec](#psexec)
   - [PsGetSid](#psgetsid)
   - [PsKill](#pskill)
   - [PsList](#pslist)
   - [PsService](#psservice)
   - [PsSuspend](#pssuspend)
   - [PsTools (Suite)](#pstools-suite)
   - [ShellRunas](#shellrunas)
   - [VMMap](#vmmap)

4. [Utilitaires de sécurité](#utilitaires-de-sécurité)
   - [Autologon](#autologon)
   - [LogonSessions](#logonsessions)
   - [NewSID (Attention : Outil obsolète)](#newsid-attention--outil-obsolète)
   - [PsLoggedOn](#psloggedon)
   - [PsLogList](#psloglist)
   - [RootkitRevealer (Attention : Outil obsolète)](#rootkitrevealer-attention--outil-obsolète)
   - [Sysmon](#sysmon)

5. [Utilitaires d’informations système](#utilitaires-dinformations-système)
   - [ClockRes](#clockres)
   - [Coreinfo](#coreinfo)
   - [LiveKd](#livekd)
   - [LoadOrder](#loadorder)
   - [ProcFeatures (Attention : Outil retiré)](#procfeatures-attention--outil-retiré)
   - [PsInfo (inclus dans la suite PsTools)](#psinfo-inclus-dans-la-suite-pstools)
   - [RAMMap](#rammap)
   - [WinObj](#winobj)

6. [Utilitaires divers](#utilitaires-divers)
   - [BgInfo](#bginfo)
   - [BlueScreen (Écran de veille)](#bluescreen-écran-de-veille)
   - [CpuStres](#cpustres)
   - [Ctrl2Cap](#ctrl2cap)
   - [DebugView](#debugview)
   - [Desktops](#desktops)
   - [Hex2dec](#hex2dec)
   - [NotMyFault](#notmyfault)
   - [PsPasswd (inclus dans la suite PsTools)](#pspasswd-inclus-dans-la-suite-pstools)
   - [PsShutdown (inclus dans la suite PsTools)](#psshutdown-inclus-dans-la-suite-pstools)
   - [RDCMan (Remote Desktop Connection Manager)](#rdcman-remote-desktop-connection-manager)
   - [RegDelNull](#regdelnull)
   - [RU (Registry Usage)](#ru-registry-usage)
   - [RegHide](#reghide)
   - [RegJump](#regjump)
   - [Strings](#strings)
   - [Testlimit](#testlimit)
   - [ZoomIt](#zoomit)

7. [Sysinternals Suite](#sysinternals-suite)

## Utilitaires de fichiers et de disques

### AccessChk
**Résumé** : Un outil en ligne de commande ultra-rapide pour vérifier les droits d'accès effectifs des utilisateurs ou des groupes sur une vaste gamme de ressources : fichiers, répertoires, clés de registre, services Windows, processus ou objets globaux. Contrairement aux outils graphiques, il permet de lister instantanément "qui peut faire quoi" sur l'ensemble d'une arborescence.

**Exemple** : Vous voulez savoir à quels services Windows un utilisateur standard (groupe "Users") possède des droits d'écriture pour identifier des failles de sécurité potentielles.

```
accesschk users -cw *
```
- Documentation : [AccessChk sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/accesschk)

- Téléchargement : [AccessChk.zip](https://download.sysinternals.com/files/AccessChk.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\accesschk.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.AccessChk
```

---

### AccessEnum
**Résumé** : Un outil graphique simple et efficace qui analyse les répertoires et les clés de registre pour afficher les autorisations de sécurité. Il permet d'identifier rapidement les fichiers ou dossiers qui possèdent des paramètres de sécurité différents de ceux de leur dossier parent, facilitant ainsi la détection de failles de sécurité ou de partages trop permissifs.

**Exemple** : Vous souhaitez vérifier rapidement si des utilisateurs ont des droits d'accès imprévus sur un dossier partagé contenant des données sensibles. En lançant AccessEnum sur ce dossier, vous verrez immédiatement une liste claire des comptes ayant des droits de lecture ou d'écriture.

- Documentation : [AccessEnum sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/accessenum)

- Téléchargement : [AccessEnum.zip](https://download.sysinternals.com/files/AccessEnum.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\accessenum.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.AccessEnum
```

---

### CacheSet
**Résumé** : Un utilitaire permettant de manipuler les paramètres de fonctionnement du cache de fichiers système de Windows. Il offre un contrôle direct sur les tailles minimales et maximales de la plage de travail du cache, permettant ainsi d'influencer la manière dont le système alloue la mémoire physique aux données du système de fichiers.

**Exemple** : Vous constatez que le cache système consomme trop de RAM au détriment de vos applications, ou vous souhaitez forcer la libération de la mémoire utilisée par le cache sans redémarrer. En ouvrant CacheSet, vous pouvez cliquer sur le bouton "Clear" pour libérer immédiatement les pages mémoire occupées.

- Documentation : [CacheSet sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/cacheset)

- Téléchargement : [CacheSet.zip](https://download.sysinternals.com/files/CacheSet.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\cacheset.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.CacheSet
```

---

### Contig
**Résumé** : Un défragmenteur en ligne de commande conçu pour rendre les fichiers individuels contigus sur le disque. Contrairement aux défragmenteurs classiques qui traitent l'intégralité d'un volume, Contig permet d'optimiser spécifiquement un fichier ou un répertoire précis, ce qui est idéal pour les fichiers volumineux et fréquemment sollicités (comme les bases de données ou les disques virtuels).

**Exemple** : Vous avez un fichier de base de données volumineux ou un fichier d'image disque virtuel (.vhdx) qui est fortement fragmenté et ralentit les performances. Vous pouvez défragmenter uniquement ce fichier spécifique sans lancer une analyse complète du disque :

```
contig -v C:\VMs\MonDisqueVirtuel.vhdx
```
- Documentation : [Contig sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/contig)
- Téléchargement : [Contig.zip](https://download.sysinternals.com/files/Contig.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\contig.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Contig
```

---

### Disk2vhd
**Résumé** : Un utilitaire pratique qui crée des versions VHD (Virtual Hard Disk) de disques physiques pour une utilisation dans des machines virtuelles Microsoft Virtual PC ou Hyper-V. Sa particularité est qu'il peut être exécuté sur un système en ligne (allumé) grâce à la technologie Volume Snapshot de Windows, permettant de créer des instantanés cohérents des volumes sans interruption de service.

**Exemple** : Vous souhaitez convertir votre serveur physique actuel en machine virtuelle pour faire des tests ou pour une migration P2V (Physical-to-Virtual). Vous lancez Disk2vhd, sélectionnez le lecteur C:, et il génère un fichier .vhdx que vous pourrez directement attacher à une nouvelle VM Hyper-V.

- Documentation : Disk2vhd sur Microsoft Learn

- Téléchargement : Disk2vhd.zip

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\disk2vhd.exe
```

- Installation Winget :

```
winget install Microsoft.Sysinternals.Disk2vhd
```

---

### DiskExt
**Résumé** : Un utilitaire en ligne de commande qui affiche les informations de mappage entre les volumes logiques (lettres de lecteurs) et les disques physiques. Il permet de voir précisément sur quel disque physique et à quel emplacement (offset et longueur) se situent les partitions d'un volume, ce qui est particulièrement utile pour comprendre la structure des disques multi-partitions ou dynamiques.

**Exemple** : Vous voulez savoir sur quel disque physique se trouve réellement votre lecteur D: et quelle est sa position exacte sur celui-ci.

```
diskext d:
```
- Documentation : [DiskExt sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/diskext)

- Téléchargement : [DiskExt.zip](https://download.sysinternals.com/files/DiskExt.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\diskext.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.DiskExt

```
---

### DiskMon
**Résumé** : Une application qui enregistre et affiche en temps réel toute l'activité des disques durs sur un système Windows. Elle permet de visualiser les opérations de lecture et d'écriture avec leurs détails techniques (secteurs, durée, etc.). Elle peut également être réduite dans la barre d'état système pour servir de "voyant de disque" logiciel (vert pour la lecture, rouge pour l'écriture).

**Exemple** : Vous soupçonnez une application d'écrire massivement sur le disque en arrière-plan. Vous lancez DiskMon pour observer les flux de données en direct et identifier la fréquence des accès disques. Vous pouvez aussi l'utiliser avec l'option /l pour avoir une icône d'activité dans votre barre des tâches.

- Documentation : [DiskMon sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/diskmon)

- Téléchargement : [Diskmon.zip](https://download.sysinternals.com/files/Diskmon.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\diskmon.exe
```
- Installation Winget :
```
winget install Microsoft.Sysinternals.DiskMon
```
---

### DU (Disk Usage)
**Résumé** : Un utilitaire en ligne de commande qui calcule et affiche l'utilisation de l'espace disque pour un répertoire spécifié. Par défaut, il parcourt récursivement les dossiers pour donner la taille totale d'une arborescence, tout en étant capable de gérer correctement les liens physiques (hard links) pour ne pas compter plusieurs fois le même fichier.

**Exemple** : Vous voulez connaître la taille réelle occupée par le dossier "Windows" et ses sous-dossiers, en affichant les tailles en Ko :
```
du -v c:\windows
```
- Documentation : [DU sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/du)

- Téléchargement : [Du.zip](https://download.sysinternals.com/files/Du.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\du.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.DU
```

---

### DiskView
**Résumé** : Un outil graphique qui fournit une carte visuelle interactive de votre disque dur. Il permet de visualiser précisément l'emplacement physique des fichiers sur les clusters du disque. En cliquant sur une zone de la carte, vous pouvez identifier quel fichier occupe ces clusters, ou inversement, rechercher un fichier pour voir comment il est réparti sur le support.

**Exemple** : Vous souhaitez comprendre pourquoi un fichier volumineux ralentit votre système malgré une défragmentation. En utilisant DiskView, vous pouvez visualiser si ce fichier est physiquement stocké sur des secteurs endommagés ou s'il est éparpillé à des endroits stratégiques du disque.

- Documentation : [DiskView sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/diskview)

- Téléchargement : [DiskView.zip](https://download.sysinternals.com/files/DiskView.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\diskview.exe
```
- Installation Winget :
```
winget install Microsoft.Sysinternals.DiskView
```

---

### EFSDump
**Résumé** : Un utilitaire en ligne de commande qui permet de voir quels utilisateurs sont autorisés à accéder à des fichiers chiffrés via le système EFS (Encrypting File System). Il utilise les API Windows pour extraire les informations sur les comptes (noms et empreintes de certificats) possédant les clés de déchiffrement pour un fichier ou un répertoire donné.

**Exemple** : Vous avez un dossier partagé contenant des fichiers chiffrés et vous voulez vérifier exactement quels utilisateurs ont le droit de les ouvrir.
```
efsdump -s C:\DonneesSensibles
```
- Documentation : [EFSDump sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/efsdump)

- Téléchargement : [EFSDump.zip](https://download.sysinternals.com/files/EFSDump.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\efsdump.exe
```
- Installation Winget :
```
winget install Microsoft.Sysinternals.EFSDump
```

---

### jcd
**Résumé** : Un outil de navigation en ligne de commande moderne (écrit en Rust) qui améliore considérablement la commande classique `cd`. Il permet de changer de répertoire par "saut" en utilisant des correspondances partielles de noms, une recherche bidirectionnelle (vers le haut et le bas de l'arborescence) et une sélection intelligente par priorité.

**Exemple** : Vous êtes dans un sous-dossier profond et vous voulez sauter rapidement vers un dossier nommé "Projets" situé quelque part dans votre arborescence sans taper le chemin complet.
```
jcd Proj
```
*(Vous pouvez ensuite utiliser la touche `Tab` pour faire défiler les correspondances).*

- Documentation : [jcd sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/jcd)

- Téléchargement : [jcd (via GitHub)](https://github.com/microsoft/jcd/releases)

- Utilisation en ligne : (Outil principalement pour Linux/macOS, non disponible sur le partage live Windows classique)

- Installation Winget :
```
# Cet outil étant multiplateforme et récent, il n'est pas encore intégré au bundle Sysinternals standard pour Windows via Winget.
```
*Note : Cet outil est un peu particulier car il cible Linux et macOS.*

---

### LDMDump
**Résumé** : Un utilitaire spécialisé qui permet d'examiner le contenu de la base de données du Gestionnaire de disques logiques (LDM) stockée sur les disques dynamiques. Il affiche des détails techniques comme l'en-tête privé, la table des matières et la base de données d'objets (partitions, composants et volumes), offrant une visibilité que les outils standards de Windows ne permettent pas d'obtenir.

**Exemple** : Vous travaillez sur un système avec des disques dynamiques et vous souhaitez inspecter la configuration exacte de la base de données LDM du disque 0 pour diagnostiquer un problème de volume RAID ou de partitionnement.
```
ldmdump /d0
```
- Documentation : [LDMDump sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/ldmdump)

- Téléchargement : [LDMDump.zip](https://download.sysinternals.com/files/LDMDump.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\ldmdump.exe
```
- Installation Winget :
```
winget install Microsoft.Sysinternals.LDMDump
```

---

### NTFSInfo
**Résumé** : Un petit utilitaire qui affiche des informations détaillées sur les volumes NTFS. Il permet de consulter la taille des unités d'allocation (clusters), l'emplacement et la taille de la Table de Fichiers Maîtres (MFT), ainsi que la localisation de la zone réservée à la MFT (MFT-Zone). Il révèle également la taille des fichiers de métadonnées invisibles du système NTFS comme $Boot ou $Bitmap.

**Exemple** : Vous souhaitez connaître la fragmentation potentielle de votre table de fichiers ou vérifier quel pourcentage du disque est réservé exclusivement à la gestion du système de fichiers (MFT-Zone) sur votre lecteur C:.
```
ntfsinfo c
```
- Documentation : [NTFSInfo sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/ntfsinfo)

- Téléchargement : [NTFSInfo.zip](https://download.sysinternals.com/files/NTFSInfo.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\ntfsinfo.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.NTFSInfo
```

---

### PendMoves et MoveFile
**Résumé** : Ce pack contient deux outils complémentaires pour gérer les fichiers "verrouillés" par le système. PendMoves affiche la liste des fichiers dont le renommage ou la suppression a été planifié pour le prochain redémarrage du système. MoveFile permet à l'utilisateur de programmer lui-même le déplacement ou la suppression d'un fichier qui est actuellement utilisé par un programme ou par Windows au prochain démarrage.

**Exemple** : Vous n'arrivez pas à supprimer un fichier `.dll` car il est utilisé par le système. Vous pouvez programmer sa suppression automatique au prochain démarrage avec MoveFile :
```
movefile C:\chemin\fichier.dll ""
```
*(Utilisez ensuite `pendmoves` pour vérifier que l'opération est bien enregistrée).*

- Documentation : [PendMoves sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pendmoves)

- Téléchargement : [PendMoves.zip](https://download.sysinternals.com/files/PendMoves.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\pendmoves.exe 
```
et 
```
\\live.sysinternals.com\tools\movefile.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PendMoves
```
et
```
winget install Microsoft.Sysinternals.MoveFile
```

---

### RegMon
**Résumé** : RegMon (Registry Monitor) était l'utilitaire de référence pour surveiller en temps réel l'activité du Registre Windows. Il permettait de voir quelles applications accédaient à quelles clés, les données qu'elles lisaient ou écrivaient, et les erreurs rencontrées. Important : Cet outil est désormais obsolète et ses fonctionnalités ont été fusionnées dans **Process Monitor (ProcMon)**.

**Exemple** : Vous vouliez comprendre pourquoi une application perdait ses paramètres après un redémarrage. En lançant RegMon, vous pouviez filtrer sur le nom de l'application et observer en direct si elle parvenait à écrire ses clés de configuration dans `HKEY_CURRENT_USER`.

- Documentation : [RegMon sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/regmon)

- Téléchargement : *(Outil retiré, disponible via [Process Monitor](https://download.sysinternals.com/files/ProcessMonitor.zip))*

- Utilisation en ligne : *(Remplacé par procmon.exe sur `\live.sysinternals.com\tools`)*

- Installation Winget :
```
winget install Microsoft.Sysinternals.ProcessMonitor
```

---

### SDelete
**Résumé** : Un utilitaire de suppression sécurisée conforme à la norme DoD 5220.22-M du ministère de la Défense des États-Unis. Il permet de supprimer définitivement des fichiers et des répertoires, ou de nettoyer l'espace libre d'un disque logique, garantissant que les données précédemment supprimées ne pourront jamais être récupérées, même avec des outils spécialisés.

**Exemple** : Vous souhaitez supprimer définitivement un dossier confidentiel en effectuant 3 passes d'écriture pour plus de sécurité :
```
sdelete -p 3 -s C:\Documents\Confidentiel
```
*(Pour nettoyer tout l'espace libre du disque `C:` afin de rendre les anciens fichiers supprimés irrécupérables : `sdelete -c c:`)*

- Documentation : [SDelete sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/sdelete)

- Téléchargement : [SDelete.zip](https://download.sysinternals.com/files/SDelete.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\sdelete.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.SDelete
```

---

### Sigcheck
**Résumé** : Un utilitaire en ligne de commande puissant qui permet de vérifier les signatures numériques des fichiers, d'afficher les numéros de version, les informations d'horodatage et les détails des certificats. Il intègre une fonctionnalité majeure : la possibilité de vérifier le hachage d'un fichier sur VirusTotal pour détecter si un exécutable est connu comme malveillant par plus de 40 moteurs antivirus.

**Exemple** : Vous souhaitez vérifier tous les fichiers exécutables du dossier `System32` pour identifier ceux qui ne sont pas signés numériquement (souvent un signe de fichier suspect ou modifié) :
```
sigcheck -u -e c:\windows\system32
```
*(Pour vérifier un fichier spécifique sur VirusTotal et obtenir le rapport : `sigcheck -v monfichier.exe`)*

- Documentation : [Sigcheck sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/sigcheck)

- Téléchargement : [Sigcheck.zip](https://download.sysinternals.com/files/Sigcheck.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\sigcheck.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Sigcheck
```

---

### Streams
**Résumé** : Le système de fichiers NTFS permet aux fichiers de contenir plusieurs flux de données (Alternate Data Streams - ADS). Alors que le flux principal contient le contenu visible du fichier, des flux cachés peuvent stocker des métadonnées ou d'autres informations invisibles pour l'explorateur de fichiers. L'utilitaire Streams permet de lister ces flux cachés et, si nécessaire, de les supprimer.

**Exemple** : Vous avez téléchargé des fichiers sur Internet et Windows les a marqués comme "bloqués" (une métadonnée stockée dans un flux ADS nommé Zone.Identifier). Vous pouvez lister tous les flux cachés dans un répertoire pour voir quels fichiers sont concernés :
```
streams -s C:\Telechargements
```
*(Pour supprimer tous les flux cachés d'un dossier : `streams -d -s C:\Telechargements`)*

- Documentation : [Streams sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/streams)

- Téléchargement : [Streams.zip](https://download.sysinternals.com/files/Streams.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\streams.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Streams
```

---

### Sync
**Résumé** : Un utilitaire inspiré de la commande UNIX du même nom, qui permet de forcer le système d'exploitation à vider toutes les données du système de fichiers présentes dans le cache vers le disque dur. Cela garantit que toutes les données modifiées sont stockées en toute sécurité et ne seront pas perdues en cas de panne du système ou de retrait brutal d'un support amovible.

**Exemple** : Avant de débrancher une clé USB ou après une grosse session de copie de fichiers, vous souhaitez vous assurer que tout est bien écrit sur vos disques amovibles :
```
sync -r
```
*(Pour vider le cache et éjecter les lecteurs amovibles : `sync -e`)*

- Documentation : [Sync sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/sync)

- Téléchargement : [Sync.zip](https://download.sysinternals.com/files/Sync.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\sync.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Sync
```

---

### VolumeID
**Résumé** : Un utilitaire spécialisé qui permet de modifier l'identifiant de volume (Serial Number) des disques formatés en FAT ou NTFS. Contrairement à l'étiquette de volume (le nom du disque) que l'on peut changer facilement, l'ID de volume est normalement fixé lors du formatage. Cet outil permet de le personnaliser sans reformater le support.

**Exemple** : Vous avez cloné un disque et certaines applications liées à l'ID de volume ne fonctionnent plus, ou vous souhaitez simplement harmoniser les identifiants de vos partitions. Pour changer l'ID du lecteur `D:` en `1234-ABCD` :
```
volumeid d: 1234-ABCD
```
*(Note : Pour les volumes NTFS, un redémarrage est nécessaire pour que le changement soit pris en compte).*

- Documentation : [VolumeID sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/volumeid)

- Téléchargement : [VolumeID.zip](https://download.sysinternals.com/files/VolumeID.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\volumeid.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.VolumeID
```

---

## Utilitaires de mise en réseau

### AD Explorer
**Résumé** : Active Directory Explorer est une visionneuse et un éditeur avancé pour Active Directory. Il permet de naviguer facilement dans une base de données AD, de définir des favoris, et d'afficher les attributs des objets sans ouvrir de boîtes de dialogue complexes. Sa fonctionnalité phare est la possibilité de prendre des "instantanés" (snapshots) d'un annuaire pour une consultation hors ligne ou pour comparer les changements entre deux états de la base de données.

**Exemple** : Vous devez auditer les modifications effectuées dans votre annuaire Active Directory entre lundi et vendredi. Vous prenez un instantané le lundi, un second le vendredi, et vous utilisez la fonction "Compare" pour lister instantanément tous les objets ou permissions qui ont été modifiés.

- Documentation : [AD Explorer sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/adexplorer)

- Téléchargement : [AdExplorer.zip](https://download.sysinternals.com/files/AdExplorer.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\ADExplorer.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ADExplorer
```

---

### ADInsight
**Résumé** : Un outil de surveillance en temps réel du protocole LDAP (Light-weight Directory Access Protocol). Il est spécifiquement conçu pour dépanner les applications clientes Active Directory en interceptant les appels effectués vers la bibliothèque Wldap32.dll. Contrairement à un sniffer réseau, il voit les requêtes avant même qu'elles ne soient envoyées au serveur, ce qui permet d'analyser précisément ce qu'une application tente de faire.

**Exemple** : Une application métier n'arrive pas à s'authentifier sur votre domaine Active Directory. En lançant ADInsight, vous pouvez capturer en direct les requêtes LDAP envoyées par l'application et identifier immédiatement si l'erreur vient d'un filtre de recherche mal formé ou d'un attribut manquant.

- Documentation : [ADInsight sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/adinsight)

- Téléchargement : [AdInsight.zip](https://download.sysinternals.com/files/AdInsight.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\ADInsight.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ADInsight
```

---

### ADRestore
**Résumé** : Un utilitaire en ligne de commande simple mais essentiel qui permet d'énumérer et de restaurer des objets supprimés ("tombstoned") dans un domaine Active Directory. Il s'appuie sur les fonctionnalités de récupération natives introduites avec Windows Server 2003 pour redonner vie à des comptes ou des unités d'organisation supprimés par erreur.

**Exemple** : Un administrateur a supprimé accidentellement un compte utilisateur important. En lançant ADRestore sans paramètre, vous listez tous les objets supprimés. Vous pouvez ensuite cibler l'utilisateur pour le restaurer :
```
adrestore -r "NomDeLUtilisateur"
```
- Documentation : [ADRestore sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/adrestore)

- Téléchargement : [AdRestore.zip](https://download.sysinternals.com/files/AdRestore.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\adrestore.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ADRestore
```

---

### PipeList
**Résumé** : Un utilitaire en ligne de commande qui liste les "canaux nommés" (named pipes) actifs sur le système. Les canaux nommés sont utilisés pour la communication entre processus (IPC). PipeList affiche non seulement leurs noms, mais aussi le nombre maximal d'instances autorisées et le nombre d'instances actuellement ouvertes pour chaque canal.

**Exemple** : Vous développez ou dépannez une application client-serveur locale et vous voulez vérifier si le canal de communication attendu a bien été créé par le service système.
```
pipelist
```
- Documentation : [PipeList sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pipelist)

- Téléchargement : [PipeList.zip](https://download.sysinternals.com/files/PipeList.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\pipelist.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PipeList
```

---

### PsFile
**Résumé** : Un utilitaire en ligne de commande qui liste les fichiers ouverts à distance sur un système (via des partages réseau). Contrairement à la commande standard `net file`, PsFile ne tronque pas les chemins d'accès longs et permet de visualiser ces informations sur des ordinateurs distants. Il offre également la possibilité de fermer ces fichiers ouverts par leur nom ou leur identifiant.

**Exemple** : Vous souhaitez voir quels fichiers sont actuellement ouverts par des utilisateurs sur votre serveur de fichiers nommé `Serveur01` et fermer un document spécifique qui est verrouillé.
```
psfile \\Serveur01
```
*(Pour fermer un fichier verrouillé par son ID : `psfile \\Serveur01 154 -c`)*

- Documentation : [PsFile sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psfile)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psfile.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsPing
**Résumé** : Un outil de diagnostic réseau avancé qui surpasse le `ping` classique. PsPing permet non seulement d'effectuer des tests ICMP standard, mais aussi des pings TCP (pour tester l'ouverture de ports), ainsi que des mesures précises de latence et de bande passante réseau. Il peut générer des histogrammes pour visualiser la régularité des temps de réponse.

**Exemple** : Vous voulez vérifier si un serveur web répond sur le port 80 et mesurer la latence de connexion avec 100 itérations rapides :
```
psping -n 100 -i 0 -q nom-du-serveur:80
```
*(Pour tester la bande passante vers un autre ordinateur exécutant PsPing en mode serveur : `psping -b -l 8k -n 10s adresse-ip:5000`)*

- Documentation : [PsPing sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psping)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psping.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### ShareEnum
**Résumé** : Un utilitaire graphique indispensable pour auditer la sécurité des partages réseau dans votre domaine ou groupe de travail. ShareEnum analyse tous les ordinateurs accessibles sur le réseau et dresse une liste complète des partages de fichiers et d'imprimantes, tout en affichant leurs permissions de sécurité (ACL). C'est l'outil idéal pour identifier rapidement les partages dont les accès sont trop permissifs (ex: "Tout le monde" en accès complet).

**Exemple** : Vous êtes administrateur réseau et vous voulez vérifier si des utilisateurs ont créé des partages "sauvages" sur leurs postes de travail avec des droits d'accès non sécurisés. Vous lancez ShareEnum pour scanner votre domaine et obtenir un tableau récapitulatif des droits de lecture/écriture pour chaque dossier partagé détecté.

- Documentation : [ShareEnum sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/shareenum)

- Téléchargement : [ShareEnum.zip](https://download.sysinternals.com/files/ShareEnum.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\ShareEnum.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ShareEnum
```

---

### TCPView
**Résumé** : Un utilitaire graphique qui affiche en temps réel toutes les connexions réseau (TCP et UDP) actives sur votre système. Il fournit une vue beaucoup plus lisible et interactive que la commande `netstat`, en affichant le nom du processus (logiciel ou service) à l'origine de chaque connexion, les adresses locales/distantes et l'état de la connexion. Les changements sont mis en évidence par des couleurs : vert pour une nouvelle connexion, jaune pour un changement d'état et rouge pour une fermeture.

**Exemple** : Vous remarquez que votre connexion internet est saturée et vous voulez identifier instantanément quel logiciel télécharge des données en arrière-plan. TCPView vous permet de voir le débit de chaque processus et de fermer immédiatement une connexion suspecte ou de tuer le processus associé.

- Documentation : [TCPView sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/tcpview)

- Téléchargement : [TCPView.zip](https://download.sysinternals.com/files/TCPView.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\Tcpview.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.TCPView
```

---

### Whois
**Résumé** : Un utilitaire en ligne de commande qui interroge les bases de données d'enregistrement pour obtenir des informations sur un nom de domaine ou une adresse IP. Il permet de connaître le propriétaire d'un domaine, le bureau d'enregistrement (registrar), les dates de création/expiration et les serveurs de noms (DNS) associés.

**Exemple** : Vous souhaitez vérifier la date d'expiration ou les informations de contact pour le domaine `microsoft.com` :
```
whois microsoft.com
```
*(Vous pouvez également l'utiliser avec une adresse IP pour identifier l'organisation à laquelle elle appartient : `whois 66.193.254.46`)*

- Documentation : [Whois sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/whois)

- Téléchargement : [Whois.zip](https://download.sysinternals.com/files/Whois.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\whois.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Whois
```

---

## Utilitaires de processus

### Autoruns
**Résumé** : Probablement l'outil le plus complet pour gérer le démarrage de Windows. Autoruns affiche absolument tout ce qui est configuré pour se lancer automatiquement au démarrage du système ou à l'ouverture de session : logiciels, services, pilotes, tâches planifiées, extensions de l'explorateur, codecs, et bien plus encore. Il permet de désactiver ou de supprimer des entrées suspectes ou inutiles pour optimiser le PC ou débusquer des logiciels malveillants.

**Exemple** : Votre ordinateur est lent au démarrage ou affiche des messages d'erreur mystérieux après la connexion. En utilisant Autoruns, vous pouvez cocher l'option "Masquer les entrées Microsoft" pour isoler immédiatement les logiciels tiers et identifier celui qui ralentit tout.

- Documentation : [Autoruns sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/autoruns)

- Téléchargement : [Autoruns.zip](https://download.sysinternals.com/files/Autoruns.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\autoruns.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Autoruns
```

---

### Handle
**Résumé** : Un utilitaire en ligne de commande indispensable pour découvrir quel programme a ouvert un fichier ou un répertoire spécifique. Il affiche les "handles" (identificateurs de ressources) ouverts pour n'importe quel processus du système. Outre les fichiers, il peut lister les handles sur les clés de registre, les ports ou les threads, et permet même de forcer la fermeture d'un handle verrouillé.

**Exemple** : Vous essayez de supprimer un dossier mais Windows vous indique qu'il est "utilisé par un autre programme". Pour identifier le coupable :
```
handle nom_du_dossier
```
*(Pour lister tous les handles ouverts par un processus spécifique comme Firefox : `handle -p firefox`)*

- Documentation : [Handle sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/handle)

- Téléchargement : [Handle.zip](https://download.sysinternals.com/files/Handle.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\handle.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Handle
```

---

### ListDLLs
**Résumé** : Un utilitaire en ligne de commande qui liste toutes les bibliothèques de liens dynamiques (DLL) actuellement chargées dans les processus en cours d'exécution. Il permet d'identifier quelle version exacte d'une DLL est utilisée, son chemin d'accès complet, et si elle possède une signature numérique. Il est particulièrement utile pour repérer des DLL non signées ou vérifier si une DLL a été relogée (déplacée de son adresse de base).

**Exemple** : Vous voulez voir toutes les DLL chargées par le processus "Explorer" et vérifier leurs informations de version :
```
listdlls -v explorer
```
*(Pour trouver tous les processus qui utilisent une DLL spécifique, par exemple `mso.dll` : `listdlls -d mso.dll`)*

- Documentation : [ListDLLs sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/listdlls)

- Téléchargement : [ListDLLs.zip](https://download.sysinternals.com/files/ListDLLs.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\listdlls.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ListDLLs
```

---

### Portmon
**Résumé** : Un utilitaire spécialisé dans la surveillance et l'affichage en temps réel de toute l'activité des ports série (COM) et parallèle (LPT) du système. Il capture les commandes de contrôle (IOCTL) et les données échangées, ce qui en fait un outil essentiel pour dépanner des périphériques matériels (modems, imprimantes spécialisées, automates industriels) ou analyser la communication des logiciels avec ces ports.

**Exemple** : Vous connectez un lecteur de code-barres sur un port COM mais le logiciel de gestion ne reçoit aucune donnée. En lançant Portmon et en sélectionnant le port concerné, vous pouvez voir si des données transitent réellement ou si le port est mal configuré par l'application (vitesse, bits de données, etc.).

- Documentation : [Portmon sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/portmon)

- Téléchargement : [Portmon.zip](https://download.sysinternals.com/files/Portmon.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\portmon.exe
```

- Installation Winget :  
*Portmon n'est pas disponible via le manifeste officiel Winget car il est considéré comme un outil "legacy" (pour versions antérieures de Windows).*

---

### ProcDump
**Résumé** : Un utilitaire en ligne de commande puissant dont l'objectif principal est de surveiller les processus pour détecter des pics d'utilisation du processeur (CPU) ou des blocages, et de générer automatiquement des fichiers de vidage de mémoire (crash dumps). Ces fichiers sont essentiels pour les développeurs et les administrateurs système afin de diagnostiquer la cause exacte d'un plantage, d'une fuite de mémoire ou d'une application qui ne répond plus.

**Exemple** : Vous avez une application nommée `monapp.exe` qui ralentit le système de manière intermittente. Vous voulez capturer un vidage complet de la mémoire dès qu'elle dépasse 80 % d'utilisation du CPU pendant au moins 5 secondes :
```
procdump -ma -c 80 -s 5 monapp.exe
```
*(Pour capturer un vidage dès qu'une application plante avec une exception : `procdump -ma -e monapp.exe`)*

- Documentation : [ProcDump sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/procdump)

- Téléchargement : [ProcDump.zip](https://download.sysinternals.com/files/Procdump.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\procdump.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ProcDump
```

---

### Process Explorer
**Résumé** : Probablement l'outil le plus célèbre de la suite. Process Explorer est un gestionnaire de processus ultra-complet qui affiche une arborescence hiérarchique des processus actifs. Il permet de voir en détail quelles DLL sont chargées par un programme, quels fichiers ou clés de registre il verrouille (handles), et offre des graphiques de performance très précis. Il intègre également une vérification VirusTotal pour scanner tous les processus en cours en un clic.

**Exemple** : Vous ne parvenez pas à supprimer un fichier car il est "ouvert dans un autre programme". Au lieu de deviner, vous utilisez la fonction de recherche (la loupe) de Process Explorer pour trouver instantanément le nom du processus exact qui détient le handle sur ce fichier.

- Documentation : [Process Explorer sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/process-explorer)

- Téléchargement : [ProcessExplorer.zip](https://download.sysinternals.com/files/ProcessExplorer.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\procexp.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ProcessExplorer
```

---

### Process Monitor
**Résumé** : Le "couteau suisse" ultime pour le dépannage système. Process Monitor fusionne les anciens outils Filemon (activité fichiers) et Regmon (activité registre) pour offrir une surveillance en temps réel de toute l'activité du système de fichiers, du registre, des processus et des threads. Il permet de voir exactement quel fichier est lu, quelle clé de registre est modifiée, et quel processus en est responsable, avec un niveau de détail granulaire (piles d'appels, utilisateurs, etc.).

**Exemple** : Une application affiche un message d'erreur générique "Accès refusé" sans préciser quel fichier pose problème. En lançant ProcMon avec un filtre sur le nom du processus, vous identifiez instantanément la ligne rouge indiquant un résultat `ACCESS DENIED` sur un fichier spécifique ou une clé de registre manquante.

Documentation : [Process Monitor sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/procmon)

Téléchargement : [ProcessMonitor.zip](https://download.sysinternals.com/files/ProcessMonitor.zip)

Utilisation en ligne :
```
\\live.sysinternals.com\tools\procmon.exe
```

Installation Winget :
```
winget install Microsoft.Sysinternals.ProcessMonitor
```

---

### PsExec
**Résumé** : Un utilitaire de ligne de commande extrêmement léger et puissant qui permet d'exécuter des processus sur des systèmes distants sans avoir à installer manuellement de logiciel client. Il est souvent utilisé pour lancer des invites de commande interactives ou des outils de diagnostic (comme `ipconfig`) sur d'autres ordinateurs du réseau. Il permet également d'exécuter des programmes localement avec les privilèges du compte **Système** (NT AUTHORITY\SYSTEM), ce qui est très utile pour accéder à certaines clés de registre protégées.

**Exemple** : Vous devez dépanner un serveur distant nommé `Serveur02` et vous voulez ouvrir une invite de commande directement sur celui-ci depuis votre poste :
```
psexec \\Serveur02 cmd
```
*(Pour lancer l'éditeur de registre localement avec les droits système maximum : `psexec -i -s regedit.exe`)*

- Documentation : PsExec sur Microsoft Learn

- Téléchargement : PSTools.zip

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psexec.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsGetSid
**Résumé** : Un utilitaire de ligne de commande qui permet de traduire les identifiants de sécurité (SID) en noms de compte lisibles (utilisateurs ou groupes) et vice-versa. Il est capable d'interroger des comptes locaux, des comptes de domaine ou même des comptes intégrés (comme "Système"). Il peut également afficher le SID d'un ordinateur distant, ce qui est utile pour vérifier si des machines clonées ont bien des SID uniques.

**Exemple** : Vous avez un SID (ex: `S-1-5-21-...`) trouvé dans un journal d'audit et vous voulez savoir à quel utilisateur il correspond :
```
psgetsid S-1-5-21-xxxxxxxxxx-xxxxxxxxxx-xxxxxxxxxx-xxxx
```
(Pour obtenir le SID de l'utilisateur "Administrateur" sur un serveur distant nommé "SRV-DATA" : psgetsid \\SRV-DATA Administrateur)

- Documentation : [PsGetSid sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psgetsid)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psgetsid.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsKill
**Résumé** : Un utilitaire en ligne de commande conçu pour arrêter (tuer) des processus récalcitrants ou inutiles. Sa force principale réside dans sa capacité à arrêter des processus non seulement sur la machine locale, mais aussi sur des ordinateurs distants sans nécessiter l'installation préalable d'un agent. Il peut cibler un processus par son nom ou par son identifiant unique (PID) et permet également de supprimer toute une arborescence de processus liés.

**Exemple** : Vous voulez arrêter de force toutes les instances de l'application "Outlook" qui ne répond plus sur votre poste :
```
pskill outlook
```
*(Pour arrêter un processus avec le PID 1234 et tous ses processus enfants sur un serveur distant nommé "SRV-APPS" : `pskill -t \\SRV-APPS 1234`)*

- Documentation : [PsKill sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pskill)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\pskill.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsList
**Résumé** : Un utilitaire en ligne de commande qui permet d'afficher des informations détaillées sur les processus en cours d'exécution, de manière similaire au Gestionnaire des tâches, mais avec la flexibilité de la console. Il peut lister les processus locaux ou distants, afficher l'arborescence des processus (liens parent-enfant), et fournir des statistiques précises sur l'utilisation de la mémoire et des threads.

**Exemple** : Vous voulez surveiller en temps réel l'utilisation des ressources d'un serveur distant nommé `SRV-WEB` avec un rafraîchissement toutes les 2 secondes :
```
pslist -s 2 \\SRV-WEB
```
*(Pour afficher l'arborescence complète des processus sur votre machine locale : `pslist -t`)*

- Documentation : [PsList sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pslist)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\pslist.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsService
**Résumé** : Un utilitaire en ligne de commande complet pour visualiser et contrôler les services Windows. Proche de la commande native `sc`, il permet d'afficher l'état, la configuration et les dépendances des services, tout en offrant la possibilité de les démarrer, arrêter, mettre en pause ou redémarrer. Sa particularité est de pouvoir s'exécuter sur des systèmes distants avec des identifiants différents et de posséder une fonction de recherche unique pour localiser les instances d'un service spécifique sur tout votre réseau.

**Exemple** : Vous souhaitez redémarrer le service de spooler d'impression sur un serveur distant nommé `SRV-PRINT` car les impressions sont bloquées :
```
psservice \\SRV-PRINT restart spooler
```
*(Pour rechercher tous les serveurs exécutant un service spécifique sur votre réseau, par exemple DHCP : `psservice find dhcp`)*

- Documentation : [PsService sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psservice)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psservice.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsSuspend
**Résumé** : Un utilitaire en ligne de commande très pratique qui permet de mettre en pause (suspendre) un processus en cours d'exécution sans l'arrêter définitivement. C'est l'outil idéal lorsqu'un programme consomme trop de ressources (CPU, disque, réseau) et que vous souhaitez libérer ces ressources temporairement pour une autre tâche, tout en gardant la possibilité de reprendre le travail là où il s'était arrêté. Il fonctionne aussi bien sur la machine locale que sur des ordinateurs distants.

**Exemple** : Une compression de fichier très lourde ralentit tout votre système. Au lieu de l'annuler, vous suspendez le processus `7z.exe` pour finir votre visioconférence, puis vous le relancez après :
```
pssuspend 7z.exe
```
*(Pour reprendre le processus mis en pause : `pssuspend -r 7z.exe`)*

- Documentation : [PsSuspend sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pssuspend)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\pssuspend.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsTools (Suite)
**Résumé** : PsTools est une collection incontournable d'utilitaires en ligne de commande permettant d'administrer des systèmes Windows locaux et, surtout, distants. Contrairement aux outils standards, les PsTools ne nécessitent l'installation d'aucun logiciel client sur les machines cibles. Ils couvrent un large éventail de tâches : exécution de processus, gestion des services, arrêt de machines, modification de mots de passe, et collecte d'informations système.

**Liste des outils inclus :**

- **PsExec** : Exécution de processus à distance.

- **PsFile** : Liste les fichiers ouverts à distance.

- **PsGetSid** : Affiche le SID d'un ordinateur ou d'un utilisateur.

- **PsInfo** : Fournit des informations détaillées sur le système.

- **PsKill** : Arrête des processus par nom ou ID.

- **PsList** : Affiche des statistiques détaillées sur les processus.

- **PsLoggedOn** : Indique qui est connecté localement ou via le réseau.

- **PsLogList** : Extrait les enregistrements des journaux d'événements.

- **PsPasswd** : Change les mots de passe des comptes.

- **PsPing** : Mesure les performances et la latence réseau.

- **PsService** : Visualise et contrôle les services.

- **PsShutdown** : Éteint ou redémarre un ordinateur.

- **PsSuspend** : Suspend ou reprend des processus.

- **Exemple** : Vous souhaitez obtenir les informations système (version d'OS, uptime, processeur) d'un ordinateur distant nommé `PC-SALLE-01` :
```
psinfo \\PC-SALLE-01
```
- Documentation : [PsTools sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pstools)

- Téléchargement : [PSTools.zip (Suite complète)](https://download.sysinternals.com/files/PSTools.zip)

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### ShellRunas
**Résumé** : Alors que la commande native `runas` de Windows s'utilise uniquement en ligne de commande, **ShellRunas** apporte cette fonctionnalité directement dans l'interface graphique. Il ajoute une entrée "Exécuter en tant qu'utilisateur différent..." au menu contextuel (clic droit) de l'Explorateur de fichiers. C'est l'outil idéal pour tester rapidement des permissions ou lancer des applications avec des comptes de service sans quitter l'interface visuelle.

**Exemple** : Vous êtes connecté avec votre compte standard et vous devez ouvrir l'Éditeur de registre avec un compte administrateur spécifique. Après avoir installé l'outil, il vous suffit de faire un clic droit sur regedit.exe et de choisir "Exécuter en tant qu'un autre utilisateur" pour saisir les identifiants requis.

- Documentation : [ShellRunas sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/shellrunas)

- Téléchargement : [ShellRunas.zip](https://download.sysinternals.com/files/ShellRunas.zip)

- Installation (pour ajouter au clic droit) :
```
shellrunas /reg
```
- Installation Winget :
```
winget install Microsoft.Sysinternals.ShellRunas
```

---

### VMMap
**Résumé** : Un utilitaire d'analyse approfondie de la mémoire virtuelle et physique pour les processus individuels. VMMap décompose l'utilisation de la mémoire d'un programme en différentes catégories (code exécutable, tas, pile, fichiers mappés, etc.). C'est l'outil de référence pour les développeurs et les experts en système qui cherchent à comprendre comment une application consomme ses ressources ou à identifier précisément l'origine d'une fuite de mémoire.

**Exemple** : Vous développez une application qui semble consommer de plus en plus de RAM au fil du temps. En utilisant VMMap, vous pouvez comparer deux instantanés de la mémoire à différents moments pour voir quel segment (par exemple le "Heap") augmente anormalement, confirmant ainsi une fuite de mémoire.

- Documentation : [VMMap sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/vmmap)

- Téléchargement : [VMMap.zip](https://download.sysinternals.com/files/VMMap.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\vmmap.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.VMMap
```

---

## Utilitaires de sécurité

### Autologon
**Résumé** : Un utilitaire simple et efficace pour configurer l'ouverture de session automatique (Auto Log On) de Windows. Au lieu de modifier manuellement le Registre, ce programme permet de saisir le nom d'utilisateur, le domaine et le mot de passe. Ces informations sont ensuite chiffrées et stockées en tant que secret LSA dans le Registre, permettant au système de se connecter automatiquement au démarrage sans intervention humaine.

**Exemple** : Vous configurez une borne interactive ou un serveur d'affichage public qui doit s'ouvrir directement sur une session utilisateur spécifique après chaque redémarrage (ou coupure de courant). Autologon vous permet de configurer cela en quelques secondes via son interface graphique ou par ligne de commande.

- Documentation : [Autologon sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/autologon)

- Téléchargement : [Autologon.zip](https://download.sysinternals.com/files/Autologon.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\autologon.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Autologon
```

---

### LogonSessions
**Résumé** : Un utilitaire en ligne de commande qui révèle toutes les sessions de connexion actuellement actives sur un système. Contrairement à ce que l'on pourrait penser, il n'y a pas qu'une seule session (la vôtre) ; Windows en crée de nombreuses pour les services et les comptes système. LogonSessions affiche pour chaque session le nom d'utilisateur, le package d'authentification utilisé (Kerberos, NTLM, etc.), le type de session (Interactive, Service, Réseau) et, en option, les processus rattachés.

**Exemple** : Vous soupçonnez qu'un compte de service ou un utilisateur fantôme exécute des tâches en arrière-plan. Pour voir toutes les sessions et les programmes qui y tournent :
```
logonsessions -p
```
*(Le paramètre `-p` permet de lister les processus spécifiques à chaque session détectée.)*

- Documentation : [LogonSessions sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/logonsessions)

- Téléchargement : [LogonSessions.zip](https://download.sysinternals.com/files/LogonSessions.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\logonsessions.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.LogonSessions
```

---

### NewSID (Attention : Outil obsolète)
**Résumé** : NewSID était un utilitaire conçu pour changer l'identifiant de sécurité (SID) d'un ordinateur après qu'il a été cloné. L'objectif était d'éviter les conflits de SID identiques sur un réseau. Cependant, Mark Russinovich (créateur de Sysinternals) a fini par démontrer que la duplication du SID de la machine ne posait pas les problèmes de sécurité que l'on craignait. En conséquence, **NewSID a été mis hors service** et n'est plus officiellement disponible en téléchargement.

**Statut actuel** : **Retiré**. Microsoft ne prend plus en charge l'utilisation de NewSID pour préparer des images système.

Alternative recommandée : Microsoft préconise désormais l'utilisation de l'outil natif Sysprep (System Preparation Tool), inclus dans Windows, pour préparer une installation en vue d'un clonage ou d'un déploiement. Sysprep réinitialise proprement le SID et d'autres paramètres spécifiques à la machine.

- Documentation : [NewSID sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/newsid)

- Article explicatif : [NewSID Retirement and the Machine SID Duplication Myth](https://techcommunity.microsoft.com/t5/sysinternals-blog/newsid-retirement-and-the-machine-sid-duplication-myth/ba-p/167512)

---

### PsLoggedOn
**Résumé** : Un utilitaire de ligne de commande indispensable pour identifier qui est actuellement connecté à un système, que ce soit localement (session ouverte sur la machine) ou à distance via des partages de ressources réseau (sessions SMB). Contrairement aux commandes Windows natives, il peut interroger un ordinateur distant pour lister ses utilisateurs actifs ou, inversement, rechercher sur tout le réseau pour localiser sur quel poste un utilisateur spécifique est connecté.

**Exemple** : Vous devez redémarrer un serveur de fichiers nommé `SRV-S01` et vous voulez vérifier qu'aucun utilisateur n'a de session ouverte pour éviter des pertes de données :
```
psloggedon \\SRV-S01
```
*(Pour savoir sur quels ordinateurs du réseau l'utilisateur "jean.dupont" est actuellement connecté : `psloggedon jean.dupont`)*

- Documentation : PsLoggedOn sur Microsoft Learn

- Téléchargement : PSTools.zip

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psloggedon.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsLogList
**Résumé** : Un utilitaire puissant en ligne de commande qui permet de consulter, filtrer et exporter les journaux d'événements (Event Logs) de Windows, aussi bien sur la machine locale que sur des ordinateurs distants. Il est particulièrement utile pour extraire rapidement des informations spécifiques (erreurs, avertissements, IDs d'événements) sans passer par l'interface lourde de l'Observateur d'événements, et permet d'exporter les résultats dans un format facile à traiter (CSV par exemple).

**Exemple** : Vous voulez lister les 10 derniers avertissements (warnings) du journal Système sur un serveur distant nommé `SRV-WEB` :
```
psloglist \\SRV-WEB -n 10 -f w system
```
*(Pour surveiller en temps réel les nouveaux événements qui arrivent sur votre machine locale : `psloglist -w system`)*

- Documentation : PsLogList sur Microsoft Learn

- Téléchargement : PSTools.zip

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psloglist.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### RootkitRevealer (Attention : Outil obsolète)
**Résumé** : RootkitRevealer était un utilitaire de détection avancé conçu pour débusquer les rootkits persistants. Il fonctionnait en comparant les résultats des API Windows standard (ce que le système "veut bien montrer") avec une analyse brute des structures du système de fichiers et du Registre (ce qui est "réellement" sur le disque). Les différences trouvées pouvaient indiquer la présence d'un malware tentant de se dissimuler.

**Statut actuel** : **Obsolète**. L'outil n'a pas été mis à jour depuis 2006. Il a été conçu pour Windows XP et Windows Server 2003 (versions 32 bits uniquement). Il ne fonctionne pas sur les versions modernes de Windows (Windows 10, 11) en raison des changements majeurs dans l'architecture du noyau et des protections contre les rootkits désormais intégrées.

**Alternative recommandée** :

- **Windows Defender** (intégré à Windows) possède désormais des capacités de détection de rootkits bien supérieures.

- Pour une analyse plus poussée avec Sysinternals, utilisez Process Monitor et Autoruns (en activant l'intégration VirusTotal) pour repérer des comportements suspects ou des entrées de démarrage masquées.

- Documentation : [RootkitRevealer sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/rootkit-revealer)

- Téléchargement (Archives) : [RootkitRevealer.zip](https://download.sysinternals.com/files/RootkitRevealer.zip)

---

### Sysmon
**Résumé** : Sysmon est un service système et un pilote de périphérique Windows qui reste actif après les redémarrages pour surveiller et journaliser l'activité du système dans le journal des événements Windows. Il fournit des informations très détaillées sur les créations de processus (avec la ligne de commande complète), les connexions réseau, et les modifications de fichiers. C'est un outil indispensable pour la sécurité et l'investigation numérique (forensics), car il permet de détecter des comportements anormaux ou malveillants souvent invisibles dans les journaux standards.

**Exemple** : Vous voulez surveiller toute création de processus et enregistrer les hachages SHA256 des fichiers exécutables pour les comparer à des bases de données de menaces. Vous installez Sysmon avec une configuration personnalisée :
```
sysmon -i c:\config\ma_config.xml -accepteula
```
*(Pour simplement installer l'outil avec les paramètres par défaut : `sysmon -i`)*

- Documentation : [Sysmon sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/sysmon)

- Téléchargement : [Sysmon.zip](https://download.sysinternals.com/files/Sysmon.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\sysmon.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Sysmon
```

---

## Utilitaires d’informations système

### ClockRes
**Résumé** : Un utilitaire très simple en ligne de commande qui affiche la résolution actuelle, minimale et maximale de l'horloge système de Windows. Cette valeur détermine la fréquence à laquelle Windows met à jour l'horloge et interrompt les processus pour le multitâche. C'est un outil utile pour les développeurs qui ont besoin de mesures de temps précises ou pour diagnostiquer des problèmes de performance liés à la latence du minuteur.

**Exemple** : Vous voulez savoir si une application gourmande a modifié la résolution de l'horloge système (souvent pour passer de 15,6 ms à 1 ms ou 0,5 ms pour gagner en réactivité) :
clockres
- Documentation : [ClockRes sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/clockres)

- Téléchargement : [ClockRes.zip](https://download.sysinternals.com/files/ClockRes.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\clockres.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ClockRes
```

---

### Coreinfo
**Résumé** : Coreinfo est un utilitaire de diagnostic qui fournit des informations extrêmement détaillées sur la topologie du processeur et de la mémoire de votre système. Il permet de visualiser le mappage entre les processeurs logiques et physiques, les nœuds NUMA, les sockets, ainsi que la hiérarchie des caches (L1, L2, L3). De plus, il liste l'ensemble des fonctionnalités et extensions supportées par le CPU (comme les instructions SSE, AVX, AES ou les capacités de virtualisation VT-x/AMD-V).

**Exemple** : Vous voulez vérifier si votre processeur supporte la virtualisation matérielle ou les instructions AES pour le chiffrement :
```
coreinfo
```
*(Pour obtenir une vue détaillée de la hiérarchie du cache et des nœuds NUMA : `coreinfo -c -n`)*

- Documentation : [Coreinfo sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/coreinfo)

- Téléchargement : [Coreinfo.zip](https://download.sysinternals.com/files/Coreinfo.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\coreinfo.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Coreinfo
```

---

### LiveKd
**Résumé** : Un utilitaire avancé qui permet d'utiliser les débogueurs de noyau de Microsoft (KD ou WinDbg) sur un système Windows en cours d'exécution, sans avoir à redémarrer en mode débogage ou à utiliser une machine tierce. LiveKd crée une vue "virtuelle" de la mémoire du noyau (un snapshot) que le débogueur peut analyser comme s'il s'agissait d'un fichier de vidage d'incident (crash dump), mais sur un système "vivant". C'est un outil précieux pour explorer les structures internes du système d'exploitation ou diagnostiquer des problèmes complexes au niveau du noyau.

**Exemple** : Vous souhaitez examiner les piles de threads du noyau ou les structures de données système sur votre machine actuelle avec l'interface graphique de WinDbg :
```
livekd -w
```
*(Pour générer un fichier de vidage complet de la mémoire du noyau sur le disque sans lancer le débogueur : `livekd -o C:\temp\kernel.dmp`)*

**Note importante** : Nécessite l'installation préalable des "Debugging Tools for Windows" (inclus dans le Windows SDK).

- Documentation : [LiveKd sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/livekd)

- Téléchargement : [LiveKd.zip](https://download.sysinternals.com/files/LiveKd.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\livekd.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.LiveKd
```

---

### LoadOrder
**Résumé** : Un petit utilitaire graphique qui affiche l'ordre exact dans lequel Windows charge les pilotes de périphérique (drivers) et les services lors du démarrage du système. Il calcule cet ordre en fonction des groupes de chargement et des dépendances définis dans le Registre. C'est un outil précieux pour diagnostiquer des problèmes de démarrage, notamment lorsqu'un pilote semble bloquer le chargement du système ou pour comprendre les priorités de lancement entre différents composants.

**Exemple** : Votre système met beaucoup de temps à démarrer ou échoue à charger un service réseau. En utilisant LoadOrder, vous pouvez vérifier si les pilotes de carte réseau ou les protocoles de bas niveau sont bien chargés avant le service en question.

Documentation : [LoadOrder sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/loadorder)

Téléchargement : [LoadOrder.zip](https://download.sysinternals.com/files/LoadOrder.zip)

Utilisation en ligne :
```
\\live.sysinternals.com\tools\loadorder.exe
```

Installation Winget :
```
winget install Microsoft.Sysinternals.LoadOrder
```

---

### ProcFeatures (Attention : Outil retiré)
**Résumé** : ProcFeatures était un petit utilitaire de ligne de commande qui signalait les capacités du processeur en matière de protection contre l'exécution de données (NX/DEP) et de traduction d'adresses physiques (PAE).

**Statut actuel** : **Retiré**. Cet outil a été officiellement mis à la retraite par Microsoft en septembre 2011. Il n'est plus disponible en téléchargement car il est devenu totalement obsolète.

**Alternative recommandée** : Toutes les fonctionnalités de ProcFeatures ont été intégrées et largement dépassées par l'outil Coreinfo (déjà présenté précédemment). Coreinfo fournit désormais des informations bien plus complètes sur les extensions du processeur, incluant le support DEP, PAE, et bien d'autres.

Documentation : [ProcFeatures sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/procfeatures)

Outil de remplacement : [Coreinfo](https://learn.microsoft.com/fr-fr/sysinternals/downloads/coreinfo)

---

### PsInfo (inclus dans la suite PsTools)
**Résumé** : Un outil en ligne de commande qui rassemble et affiche des informations essentielles sur le système Windows local ou distant. Il fournit en un coup d'œil des détails tels que la version du noyau, le type de produit, le temps d'activité (uptime), la quantité de RAM, le processeur, ainsi que la date d'installation. Il est particulièrement apprécié des administrateurs pour inventorier rapidement les correctifs (hotfixes) ou les logiciels installés sur les machines du réseau.

**Exemple** : Vous voulez auditer un serveur distant nommé `SRV-CORP` pour lister ses logiciels installés et ses correctifs de sécurité :
```
psinfo \\SRV-CORP -s -h
```
*(Pour obtenir uniquement les informations sur l'espace disque de votre machine locale : `psinfo -d`)*

- Documentation : [PsInfo sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psinfo)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psinfo.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### RAMMap
**Résumé** : RAMMap est un utilitaire d'analyse de la mémoire physique extrêmement détaillé. Là où le Gestionnaire des tâches reste superficiel, RAMMap montre exactement comment Windows alloue la RAM : quelle quantité est utilisée par le noyau, par les pilotes, ou pour mettre en cache des fichiers spécifiques. Il permet de visualiser les "Working Sets" des processus, les listes de veille (Standby list) et même les adresses physiques de la mémoire. C'est l'outil ultime pour diagnostiquer les problèmes de "pression mémoire" ou comprendre pourquoi votre RAM semble pleine alors qu'aucun gros processus n'est visible.

**Exemple** : Vous constatez que votre système est lent et que la RAM est saturée. En ouvrant RAMMap, vous allez dans l'onglet "File Summary" et découvrez qu'un fichier de base de données de plusieurs Go est entièrement chargé dans le cache système (Metafile), expliquant ainsi l'absence de mémoire libre pour vos applications. *(Astuce : Le menu "Empty" permet de vider manuellement différents types de mémoire, comme la "Standby List", pour libérer instantanément de la RAM sans redémarrer)*.

- Documentation : [RAMMap sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/rammap)

- Téléchargement : [RAMMap.zip](https://download.sysinternals.com/files/RAMMap.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\rammap.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.RAMMap
```

---

### WinObj
**Résumé** : WinObj est un explorateur graphique pour l'espace de noms du **Gestionnaire d'objets** de Windows (Object Manager). Contrairement à l'Explorateur de fichiers qui gère les dossiers et fichiers physiques, WinObj permet de visualiser les objets internes gérés par le noyau NT, tels que les terminaux de communication (Sections), les sémaphores, les mutex, les ports de message, et surtout les noms symboliques des périphériques (comme les liens entre `C:` et les partitions physiques). C'est un outil essentiel pour les développeurs système et les experts en sécurité pour comprendre comment le noyau organise ses ressources.

**Exemple** : Vous voulez comprendre à quel disque physique ou partition correspond réellement votre lecteur `C:`. En ouvrant WinObj et en naviguant dans le dossier `\Global??`, vous trouverez le lien symbolique `C:` qui pointe vers un objet de type périphérique comme `\Device\HarddiskVolume3`.

- Documentation : [WinObj sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/winobj)

- Téléchargement : [WinObj.zip](https://download.sysinternals.com/files/WinObj.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\winobj.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.WinObj
```

---

## Utilitaires divers

### BgInfo
**Résumé** : Un utilitaire pratique qui affiche automatiquement des informations clés sur la configuration d'un ordinateur (nom de la machine, adresse IP, version de l'OS, niveau de Service Pack, processeur, etc.) directement en arrière-plan sur le bureau. C'est l'outil favori des administrateurs système qui gèrent de nombreux serveurs ou machines virtuelles, car il permet d'identifier instantanément le système sur lequel on travaille sans avoir à ouvrir plusieurs fenêtres de diagnostic.

**Fonctionnement** : Contrairement à un gadget qui tourne en tâche de fond, BgInfo génère une nouvelle image bitmap fusionnant votre papier peint et les informations système, puis il quitte. Il ne consomme donc aucune ressource CPU ou RAM une fois l'image appliquée.

**Exemple** : Vous gérez un parc de serveurs via Bureau à distance (RDP). Pour éviter toute erreur de manipulation, vous configurez BgInfo pour qu'il s'affiche en haut à droite de chaque bureau avec le nom du serveur en rouge. Vous ajoutez ensuite la commande suivante dans le dossier de démarrage pour une mise à jour silencieuse à chaque connexion :
```
bginfo.exe /timer:0 /nolicprompt
```
- Documentation : [BgInfo sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/bginfo)

- Téléchargement : [BgInfo.zip](https://download.sysinternals.com/files/BGInfo.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\bginfo.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.BgInfo
```

---

### BlueScreen (Écran de veille)
**Résumé** : Probablement l'utilitaire le plus célèbre (et le plus malicieux) de Sysinternals. Ce n'est pas un outil de diagnostic, mais un écran de veille qui simule à la perfection le redoutable "Écran bleu de la mort" (BSOD). Sa force réside dans son authenticité : il extrait les informations réelles de votre système (version du noyau, pilotes chargés, adresses mémoire) pour générer un message d'erreur crédible, puis simule un redémarrage avec la barre de progression de Windows.

**Usage** : Essentiellement utilisé pour faire des farces à des collègues ou des amis, ou pour tester les nerfs d'un administrateur système.

**Fonctionnalités** :

- Simule différents types d'erreurs BSOD.

- Simule les écrans de chargement de Windows.

- Alterne entre erreur et redémarrage toutes les 15 secondes.

- Option "activité disque fictive" pour plus de réalisme.

- Documentation : [BlueScreen sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/bluescreen)

- Téléchargement : [BlueScreen.zip](https://download.sysinternals.com/files/BlueScreen.zip)

- Installation : Copier le fichier `Sysinternals Bluescreen.scr` dans `C:\Windows\System32`, puis le sélectionner dans les paramètres d'écran de veille de Windows.

- Installation Winget :
```
winget install Microsoft.Sysinternals.BlueScreen
```

---

### CpuStres
**Résumé** : CpuStres est un utilitaire de test de charge (stress test) conçu pour simuler l'activité du processeur. Il permet de lancer jusqu'à 64 threads simultanément, chacun pouvant être configuré de manière indépendante. Cet outil est idéal pour observer comment un système réagit sous une charge CPU intensive, pour tester la stabilité d'un processeur ou pour vérifier le comportement d'autres applications lorsque les ressources processeur sont saturées.

**Paramètres par thread** :

- **Niveau d'activité** : Contrôle la durée de fonctionnement par rapport au repos (Bas, Moyen, Occupé, Maximum). En mode "Maximum", le thread tourne en boucle continue.

- **Priorité** : Permet de définir la priorité du thread (IDLE, Normal, High, etc.) pour voir comment le planificateur de Windows gère la distribution des ressources.

**Exemple** : Vous voulez vérifier si le système de refroidissement de votre serveur est efficace sous une charge maximale. Vous ouvrez CpuStres, activez plusieurs threads et réglez leur activité sur "Maximum" tout en surveillant la température avec un autre outil.

- Documentation : [CpuStres sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/cpustres)

- Téléchargement : [CpuStres.zip](https://download.sysinternals.com/files/CpuStres.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\cpustres.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.CpuStres
```

---

### Ctrl2Cap
**Résumé** : Ctrl2Cap est un pilote de périphérique (driver) très léger qui permet de transformer la touche **Verr Maj** (Caps Lock) en touche **Ctrl**. Cet outil est particulièrement apprécié des anciens utilisateurs d'UNIX ou des développeurs qui préfèrent avoir la touche Ctrl à portée de doigt, à l'emplacement traditionnel du clavier des stations de travail. Contrairement à d'autres méthodes logicielles, Ctrl2Cap opère au niveau du pilote de clavier, ce qui garantit que le remappage est actif partout dans Windows.

**Usage** : Il s'utilise uniquement en ligne de commande pour l'installation et la désinstallation. Un redémarrage est nécessaire pour que les modifications prennent effet.

**Exemple** : Vous êtes fatigué d'appuyer sur la petite touche Ctrl en bas à gauche pour vos raccourcis. Vous installez le driver pour utiliser la grosse touche Verr Maj à la place :
```
ctrl2cap /install
```
*(Pour revenir à la configuration d'origine : `ctrl2cap /uninstall`)*

- Documentation : [Ctrl2Cap sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/ctrl2cap)

- Téléchargement : [Ctrl2cap.zip](https://download.sysinternals.com/files/Ctrl2cap.zip)

- Installation Winget :
```
winget install Microsoft.Sysinternals.Ctrl2Cap
```

---

### DebugView
**Résumé** : DebugView est un utilitaire qui permet de surveiller et de capturer en temps réel la sortie de débogage (messages envoyés via `OutputDebugString` pour Win32 ou `DbgPrint` pour le noyau) sur votre système local ou sur n'importe quel ordinateur du réseau via TCP/IP. Il est extrêmement utile car il permet de voir les messages de log internes des applications et des pilotes de périphériques sans avoir besoin d'installer un débogueur complet (comme WinDbg ou Visual Studio).

**Fonctionnalités clés** :

- **Double capture** : Affiche à la fois les messages provenant d'applications utilisateur (Win32) et du noyau (drivers).

- **Monitoring à distance** : Permet de voir la console de débogage d'un serveur distant.

- **Filtrage puissant** : Système d'inclusion/exclusion et mise en surbrillance par couleurs pour isoler les messages d'un processus spécifique.

- **Fichiers journaux** : Possibilité d'enregistrer la sortie dans des fichiers avec rotation automatique.

**Exemple** : Vous développez un script ou un petit utilitaire qui ne possède pas d'interface console. En insérant des fonctions de sortie de débogage dans votre code, vous pouvez ouvrir DebugView pour voir ce qui se passe "sous le capot" pendant l'exécution. *(Pour capturer les messages du noyau, n'oubliez pas de lancer DebugView en tant qu'administrateur et de cocher "Capture Kernel" dans le menu Capture)*.

Documentation : [DebugView sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/debugview)

Téléchargement : [DebugView.zip](https://download.sysinternals.com/files/DebugView.zip)

Utilisation en ligne :
```
\\live.sysinternals.com\tools\dbgview.exe
```

Installation Winget :
```
winget install Microsoft.Sysinternals.DebugView
```

---

### Desktops
**Résumé** : Cet utilitaire permet de créer jusqu'à quatre bureaux virtuels pour organiser votre espace de travail. Contrairement à beaucoup d'autres outils similaires qui se contentent de masquer ou d'afficher des fenêtres, **Desktops** utilise de véritables objets de bureau Windows natifs. Cela le rend extrêmement léger et stable, car la gestion est confiée directement au noyau Windows. Vous pouvez ainsi séparer vos activités (travail, navigation web, messagerie, etc.) sans encombrement.

**Particularités et limites** :

- **Stabilité** : En utilisant les objets de bureau natifs, il évite les bugs d'affichage fréquents sur d'autres outils.

- **Isolation** : Comme les fenêtres sont liées à un bureau à leur création, vous ne pouvez pas déplacer une fenêtre d'un bureau à un autre.

- **Persistance** : Il n'est pas possible de fermer un bureau une fois créé sans fermer la session utilisateur.

- **Barre des tâches** : Un processus `explorer.exe` distinct tourne sur chaque bureau, mais les icônes de la zone de notification (systray) n'apparaissent généralement que sur le premier bureau.

**Exemple** : Vous travaillez sur un projet complexe avec de nombreuses fenêtres ouvertes. Pour ne pas être déconcentré par vos e-mails ou Slack, vous configurez un raccourci clavier (ex: `Alt+2`) pour basculer instantanément sur un bureau vierge dédié à vos communications.

- Documentation : [Desktops sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/desktops)

- Téléchargement : [Desktops.zip](https://download.sysinternals.com/files/Desktops.zip)

- Utilisation en ligne : 
```
\\live.sysinternals.com\tools\desktops.exe
```

Installation Winget :
```
winget install Microsoft.Sysinternals.Desktops
```

---

### Hex2dec
**Résumé** : Un petit utilitaire ultra-léger en ligne de commande qui permet de convertir instantanément des nombres entre le format hexadécimal et le format décimal. C'est l'outil parfait pour les développeurs ou les administrateurs qui manipulent souvent des adresses mémoire ou des codes d'erreur et qui souhaitent éviter d'ouvrir la calculatrice Windows à chaque fois.

**Fonctionnement** :

- Si vous entrez un nombre décimal, il affiche l'équivalent hexadécimal.

- Si vous entrez un nombre précédé de `0x` ou `x`, il affiche l'équivalent décimal.

**Exemple** :

- Pour convertir la valeur décimale 1233 en hexadécimal :
```
hex2dec 1233
```
- Pour convertir la valeur hexadécimale 0x4D2 en décimal :
```
hex2dec 0x4D2
```
- Documentation : [Hex2dec sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/hex2dec)

- Téléchargement : [Hex2dec.zip](https://download.sysinternals.com/files/Hex2dec.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\hex2dec.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Hex2dec
```

---

### NotMyFault
**Résumé** : NotMyFault est un outil de diagnostic "provocateur". Il est utilisé pour causer délibérément des plantages (BSOD), des blocages du système ou des fuites de mémoire (pool leaks) dans le noyau Windows. Bien que cela puisse paraître contre-intuitif, c'est un utilitaire indispensable pour les développeurs de pilotes et les administrateurs qui souhaitent tester si leurs systèmes de récupération (comme le redémarrage automatique ou la génération de fichiers d'image mémoire/dump) fonctionnent correctement. Il sert également de base d'apprentissage pour analyser des crashs réels.

**Fonctionnalités** :

- **Crash** : Simule divers types d'erreurs fatales (débordement de tampon, corruption de pile, IRQL trop élevé, etc.).

- **Hang** : Force le système à ne plus répondre (blocage via IRP ou DPC).

- **Leak** : Provoque des fuites de mémoire dans le pool de mémoire du noyau pour observer la saturation des ressources.

**Exemple** : Vous venez de configurer un serveur pour qu'il génère un "vidage complet" sur le réseau en cas de plantage. Pour valider que cette configuration est opérationnelle sans attendre une vraie panne, vous utilisez NotMyFault pour déclencher un écran bleu immédiat :
```
notmyfaultc.exe 0x01
```
*(L'option `0x01` déclenche un crash de type "High IRQL fault")*.

- Documentation : [NotMyFault sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/notmyfault)

- Téléchargement : [NotMyFault.zip]https://download.sysinternals.com/files/NotMyFault.zip

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\notmyfault.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.NotMyFault
```

---

### PsPasswd (inclus dans la suite PsTools)
**Résumé** : Un utilitaire en ligne de commande qui permet aux administrateurs de changer le mot de passe d'un compte utilisateur (local ou de domaine) sur un ou plusieurs ordinateurs du réseau simultanément. C'est un outil précieux pour appliquer des politiques de sécurité consistant à changer régulièrement les mots de passe des administrateurs locaux sur un grand parc informatique. PsPasswd utilise les API de réinitialisation de mot de passe de Windows, garantissant que les mots de passe ne transitent jamais en clair sur le réseau.

**Exemple** : Vous devez changer le mot de passe du compte local "AdminLocal" sur tous les serveurs listés dans un fichier texte nommé `serveurs.txt` :
```
pspasswd @serveurs.txt AdminLocal NouveauMotDePasse123!
```
*(Si vous voulez changer le mot de passe sur votre machine locale : `pspasswd NomUtilisateur NouveauMotDePasse`)*

- Documentation : [PsPasswd sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/pspasswd)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\pspasswd.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### PsShutdown (inclus dans la suite PsTools)
**Résumé** : Un utilitaire en ligne de commande beaucoup plus puissant que la commande `shutdown` native de Windows. Il permet d'éteindre, de redémarrer, de mettre en veille ou de verrouiller des ordinateurs locaux ou distants. Sa grande force réside dans sa flexibilité : il peut afficher un message personnalisé aux utilisateurs, leur laisser la possibilité d'annuler l'opération, ou au contraire forcer la fermeture immédiate de toutes les applications.

**Fonctionnalités clés** :

- **Verrouillage/Déconnexion** : Peut verrouiller la session (`-l`) ou déconnecter l'utilisateur (`-o`).

- **Planification** : Permet de définir un compte à rebours (`-t nn`) ou une heure précise pour l'arrêt.

- **Annulation** : Possibilité d'annuler un arrêt imminent déjà lancé (`-a`).

- **Gestion à distance** : Capacité d'agir sur une liste d'ordinateurs via un fichier texte.

**Exemple** : Vous voulez planifier le redémarrage d'un serveur distant nommé SRV-PROD à 23h00, en affichant un message de prévention aux utilisateurs connectés :
```
psshutdown \\SRV-PROD -r -t 23:00 -m "Maintenance système prévue à 23h00. Veuillez enregistrer votre travail."
```
*(Pour forcer un arrêt immédiat sans préavis sur la machine locale : `psshutdown -k -t 0 -f`)*

- Documentation : [PsShutdown sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/psshutdown)

- Téléchargement : [PSTools.zip](https://download.sysinternals.com/files/PSTools.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\psshutdown.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.PsTools
```

---

### RDCMan (Remote Desktop Connection Manager)
**Résumé** : RDCMan est un gestionnaire puissant pour centraliser et organiser de multiples connexions Bureau à distance (RDP). Contrairement au client Windows standard qui ne gère qu'une session à la fois, cet outil permet de regrouper des centaines de serveurs dans une interface unique, avec une arborescence hiérarchique. Il est particulièrement utile pour les administrateurs de centres de données ou de laboratoires de test.

**Fonctionnalités clés** :

- **Organisation en groupes** : Permet de classer les serveurs (par projet, client ou emplacement) et de lancer une connexion/déconnexion sur tout un groupe en un clic.

- **Héritage des paramètres** : Un serveur peut hériter de ses identifiants ou de sa résolution d'affichage depuis son groupe parent, simplifiant les mises à jour massives (ex: changement de mot de passe).

- **Vue en miniatures** : Affiche un aperçu en direct de toutes les sessions actives dans un groupe sous forme de mosaïque.

- **Sécurité** : Les mots de passe sont chiffrés et stockés de manière sécurisée (CryptProtectData).

**Exemple** : Vous gérez une ferme de 20 serveurs web. Au lieu d'ouvrir 20 fenêtres RDP individuelles, vous créez un groupe "Web Cluster" dans RDCMan. Vous pouvez ainsi voir l'état de chaque serveur d'un seul coup d'œil via les miniatures et basculer instantanément de l'un à l'autre dans la même fenêtre.

- Documentation : [RDCMan sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/rdcman)

- Téléchargement : [RDCMan.zip](https://download.sysinternals.com/files/RDCMan.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\rdcman.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.RDCMan
```

---

### RegDelNull
**Résumé** : RegDelNull est un utilitaire spécialisé en ligne de commande qui permet de trouver et de supprimer des clés de Registre contenant des caractères "Null" incorporés (le caractère `\0`). Ces caractères rendent les clés de Registre invisibles ou impossibles à supprimer via les outils standards comme `Regedit`, car l'API Windows classique interprète le caractère Null comme la fin d'une chaîne de caractères. Cette technique est parfois utilisée par des malwares ou des rootkits pour cacher leurs entrées de configuration.

**Usage** : L'outil scanne le chemin spécifié et affiche les clés problématiques en remplaçant le caractère Null par un astérisque (`*`). Il demande ensuite confirmation avant toute suppression.

**Exemple** : Vous suspectez la présence d'une clé cachée dans la ruche `HKEY_LOCAL_MACHINE\SOFTWARE`. Vous lancez un scan récursif (avec l'option `-s`) pour nettoyer ces entrées :
```
regdelnull hklm\software -s
```
- Documentation : [RegDelNull sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/regdelnull)

- Téléchargement : [RegDelNull.zip](https://download.sysinternals.com/files/RegDelNull.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\regdelnull.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.RegDelNull
```

---

### RU (Registry Usage)
**Résumé** : RU est un utilitaire en ligne de commande qui permet de mesurer la consommation d'espace disque des clés du Registre Windows. À l'image de l'outil `du` (Disk Usage) pour les fichiers, RU parcourt les clés et sous-clés que vous spécifiez pour rapporter le nombre de valeurs et la taille totale qu'elles occupent. C'est un outil très utile pour identifier quelles parties du Registre sont anormalement volumineuses ou pour analyser la croissance des ruches (hives) du système.

**Fonctionnalités clés** :

- **Récursivité** : Calcule par défaut la taille cumulée d'une clé et de l'ensemble de ses sous-clés.

- **Analyse de ruches** : Peut charger et analyser directement un fichier "hive" (`-h`) sans qu'il soit monté dans le Registre actif.

- **Export CSV** : Permet de générer des rapports structurés (`-c`) pour un traitement ultérieur dans Excel ou une base de données.

**Exemple** : Vous voulez savoir quelle place occupe la configuration logicielle dans `HKEY_LOCAL_MACHINE` jusqu'à une profondeur de 2 niveaux :
```
ru -l 2 hklm\software
```
*(Pour obtenir un rapport complet de toutes les sous-clés au format CSV : `ru -v -c hklm\software`)*

- Documentation : [RU sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/ru)

- Téléchargement : [RU.zip](https://download.sysinternals.com/files/RU.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\ru.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.RU
```

---

### RegHide
**Résumé** : RegHide est un outil de démonstration qui illustre une faille de sécurité (ou une "curiosité" architecturale) dans Windows. Il utilise l'API native (NTDLL) pour créer des clés de Registre dont le nom contient des caractères nuls incorporés. Comme l'API Win32 standard interprète le caractère nul comme une fin de chaîne, ces clés deviennent invisibles et impossibles à manipuler avec les outils classiques comme `Regedit`. Cet outil sert principalement à montrer comment des malwares pourraient cacher des données dans le Registre.

**Concept technique** :

- **API Win32** : Utilise des chaînes de caractères terminées par un caractère nul (\0).

- **API Native** : Utilise des chaînes Unicode comptées (longueur explicite), ce qui permet d'inclure des caractères nuls au milieu du nom d'une clé.

**Exemple** : Vous exécutez RegHide pour créer une clé "fantôme". Si vous essayez de la voir dans l'Éditeur du Registre, elle n'apparaîtra pas ou affichera une erreur. Pour la supprimer, vous devrez utiliser un outil capable de gérer ces caractères, comme RegDelNull (vu précédemment).

- Documentation : [RegHide sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/reghide)

- Téléchargement : [RegHide.zip](https://download.sysinternals.com/files/RegHide.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\reghide.exe
```

- Installation Winget : non disponible via winget (outil de démonstration/code source).

---

### RegJump
**Résumé** : Un utilitaire extrêmement pratique en ligne de commande qui permet de gagner un temps précieux lors de l'édition du Registre. Au lieu de naviguer manuellement à travers l'arborescence complexe de `Regedit`, RegJump ouvre directement l'éditeur de registre sur le chemin spécifié. Il supporte aussi bien les noms complets des ruches (ex: `HKEY_LOCAL_MACHINE`) que leurs abréviations courantes (ex: `HKLM`).

**Fonctionnalité clé** :

- **Prise en charge du Presse-papiers** : Avec l'option -c, l'outil lit le chemin du registre directement depuis votre presse-papiers et y saute instantanément.

**Exemple** : Vous lisez un tutoriel qui vous demande de modifier une valeur dans `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`. Au lieu de cliquer sur chaque dossier dans Regedit, vous tapez simplement :
```
regjump HKCU\Software\Microsoft\Windows\CurrentVersion\Run
```
*(Ou, si vous avez copié le chemin : `regjump -c`)*

- Documentation : [RegJump sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/regjump)

- Téléchargement : [Regjump.zip](https://download.sysinternals.com/files/Regjump.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\regjump.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.RegJump
```

---

### Strings
**Résumé** : Un utilitaire en ligne de commande indispensable pour les analystes en sécurité et les développeurs. **Strings** parcourt n'importe quel fichier (exécutable, bibliothèque DLL, document, etc.) pour en extraire les séquences de caractères lisibles (chaînes de texte). Sa particularité est de pouvoir détecter aussi bien les chaînes au format **ASCII** que celles au format **UNICODE**, qui sont souvent invisibles avec les outils de recherche de texte classiques. Il est couramment utilisé pour inspecter le contenu de fichiers suspects ou pour trouver des messages d'erreur et des URLs cachés dans un programme.

**Fonctionnalités clés** :

- **Détection hybride** : Recherche simultanément l'ASCII et l'UNICODE par défaut.

- **Récursivité** : Avec l'option `-s`, il peut analyser tous les fichiers d'un répertoire et de ses sous-dossiers.

- **Personnalisation** : Vous pouvez définir la longueur minimale des chaînes à extraire (par défaut 3 caractères) avec l'option `-n`.

**Exemple** : Vous voulez inspecter un fichier exécutable inconnu `logiciel.exe` pour voir s'il contient des adresses web ou des messages suspects, tout en ignorant la bannière de l'outil :
```
strings -nobanner logiciel.exe
```
*(Pour rechercher un mot spécifique dans tous les exécutables d'un dossier : `strings * | findstr /i "mot_cle"`)*

- Documentation : Strings sur Microsoft Learn

- Téléchargement : Strings.zip

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\strings.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.Strings
```

---

### Testlimit
**Résumé** : Testlimit est un utilitaire de ligne de commande conçu pour tester la robustesse de votre système et de vos applications en simulant l'épuisement des ressources. Il permet de "stresser" volontairement Windows en accaparant massivement de la mémoire, des handles, des processus ou des threads. C'est l'outil idéal pour les développeurs et les administrateurs qui souhaitent observer comment une application se comporte lorsqu'elle manque de ressources ou pour vérifier les limites physiques et logiques d'un système.

**Fonctionnalités clés (exemples de stress)** :

- **Mémoire** : Allouer/fuir de la mémoire (`-m`), de la mémoire virtuelle (`-r`) ou de la mémoire partagée (`-s`).

- **Objets système** : Créer des milliers de handles (`-h`), de processus (`-p`) ou de threads (`-t`).

- **Interface (USER/GDI)** : Épuiser le tas du bureau (desktop heap) ou créer des objets GDI (`-g`) pour saturer l'interface graphique.

**Exemple** : Vous voulez vérifier si votre application gère correctement les erreurs d'allocation de mémoire. Vous lancez Testlimit pour consommer presque toute la RAM disponible par blocs de 100 Mo :
```
testlimit64.exe -m 100
```
*(Pour créer 10 000 handles et voir si le système reste stable : `testlimit64.exe -h -c 10000`)*

- Documentation : [Testlimit sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/testlimit)

- Téléchargement : [Testlimit.zip](https://download.sysinternals.com/files/TestLimit.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\testlimit64.exe
```

- Installation Winget : non disponible par défaut (outil de test spécifique).

---

### ZoomIt
**Résumé** : ZoomIt est l'outil indispensable pour les présentateurs, les formateurs et les créateurs de démonstrations techniques. Il permet de zoomer instantanément sur une partie de l'écran, d'annoter en direct avec un stylet virtuel (dessin de lignes, flèches, rectangles, texte) et même de transformer l'écran en tableau blanc ou noir. Depuis ses dernières versions, il permet également l'enregistrement d'écran (vidéo MP4 ou GIF) et possède une fonction de compte à rebours (Timer) pour les pauses durant les présentations.

**Fonctionnalités clés** :

- **Zoom statique et dynamique** : Zoomer sur une zone fixe ou continuer à utiliser Windows tout en étant zoomé (Live Zoom).

- **Annotations** : Dessiner des formes géométriques parfaites (Shift pour lignes, Ctrl pour rectangles, Tab pour ellipses, Ctrl+Shift pour flèches) et écrire du texte.

- **Enregistrement** : Capturer une zone ou l'intégralité de l'écran en vidéo.

- **DemoType** : Une fonction avancée pour simuler la saisie de code ou de texte durant une démo.

**Exemple** : Lors d'une réunion sur Teams, vous voulez montrer un détail précis dans un fichier Excel. Vous appuyez sur `Ctrl+1` pour zoomer, puis vous maintenez `Ctrl+Maj` en dessinant avec la souris pour pointer une cellule avec une flèche rouge. Pour finir, vous appuyez sur W pour passer sur un tableau blanc et expliquer un schéma rapide.

- Documentation : [ZoomIt sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/zoomit)

- Téléchargement : [ZoomIt.zip](https://download.sysinternals.com/files/ZoomIt.zip)

- Utilisation en ligne :
```
\\live.sysinternals.com\tools\zoomit.exe
```

- Installation Winget :
```
winget install Microsoft.Sysinternals.ZoomIt
```

---

## Sysinternals Suite
**Résumé** : La Sysinternals Suite est le pack ultime regroupant l'intégralité des utilitaires développés par Mark Russinovich et son équipe. Au lieu de télécharger chaque outil individuellement, cette suite permet d'obtenir en une seule fois plus de 70 outils de diagnostic, de sécurité et de gestion système (incluant les célèbres Process Explorer, Autoruns, PsExec, Sysmon, etc.). C'est la boîte à outils indispensable pour tout administrateur système, expert en cybersécurité ou utilisateur avancé de Windows.

**Contenu de la suite** : Elle inclut des outils classés par catégories :

- **Gestion des processus** (Process Explorer, Procmon, PsList...)

- **Sécurité** (AccessChk, Autoruns, Sigcheck, Sysmon...)

- **Réseau** (TCPView, PsPing, WhoIs...)

- **Utilitaires fichiers et disques** (SDelete, Disk2vhd, DU, Junction...)

- **Informations système** (Coreinfo, RAMMap, Handle...)

**Exemple d'usage** : Plutôt que de chercher quel outil utiliser pour réparer un PC infecté ou lent, vous copiez l'intégralité de la suite sur une clé USB. Vous avez alors immédiatement accès à Autoruns pour voir ce qui démarre avec Windows, Process Explorer pour débusquer les processus cachés et Strings pour analyser des fichiers suspects.

- Documentation : [Sysinternals Suite sur Microsoft Learn](https://learn.microsoft.com/fr-fr/sysinternals/downloads/sysinternals-suite)

- Téléchargement (Standard) : [SysinternalsSuite.zip](https://download.sysinternals.com/files/SysinternalsSuite.zip)

- Versions spécifiques : Disponible aussi pour `Nano Server` et `ARM64`.

- Installation via Microsoft Store : [Lien vers le Store](https://www.microsoft.com/store/apps/9P7KNL5RWT25)

Installation Winget :
```
winget install Microsoft.SysinternalsSuite
```

---
