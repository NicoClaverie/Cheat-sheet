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

1. [Utilitaires de fichiers et de disques](#Utilitaires-de-fichiers-et-de-disques)
2. [Utilitaires de mise en réseau](#Utilitaires-de-mise-en-réseau)
3. [Utilitaires de processus](#Utilitaires-de-processus)
4. [Utilitaires de sécurité](#Utilitaires-de-sécurité)
5. [Utilitaires d’informations système](#Utilitaires-d’informations-système)
6. [Utilitaires divers](#Utilitaires-divers)

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

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

---

###

