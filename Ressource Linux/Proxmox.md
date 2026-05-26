# Guide des 10 Commandes CLI Proxmox Essentielles pour Administrateurs

L'environnement virtuel Proxmox (VE) dispose d'une interface graphique intuitive, mais l'utilisation de l'interface en ligne de commande (CLI) est indispensable pour les configurations avancées, la création de scripts et l'automatisation. Voici les 10 commandes incontournables.

## 1. `qm` (QEMU Manager)
La commande principale pour interagir avec les machines virtuelles (VM) basées sur QEMU/KVM.

*   **Lister les VMs (affiche le statut et l'ID) :**
    ```bash
    qm list
    ```
   
*   **Créer une nouvelle VM :**
    ```bash
    qm create 103 --name "DebianVM" --memory 2048 --net0 virtio,bridge=vmbr0 --sockets 1 --cores 2 --ostype l26
    ```
    *(Crée une VM Linux nommée "DebianVM", 2 Go de RAM, 2 cœurs)*
*   **Gestion de l'alimentation :**
    ```bash
    qm start 103     # Démarre la VM 103
    qm shutdown 101  # Arrête proprement la VM 101
    qm stop 103      # Arrêt forcé (immédiat) de la VM 103
    ```
*   **Snapshots et Clonage :**
    ```bash
    qm snapshot 103 "before_upgrade" # Crée un instantané
    qm rollback 103 "before_upgrade" # Restaure l'instantané
    qm clone 103 104 --name "DebianClone" --full # Clone complet de la VM
    ```

## 2. `pve-firewall`
Gère les règles de pare-feu pour les nœuds, VMs et conteneurs Proxmox.

*   **Vérifier le statut :**
    ```bash
    pve-firewall status
    ```
   
*   **Autoriser le trafic SSH :**
    ```bash
    pve-firewall create rule -action accept -macro ssh
    ```
   

## 3. `pvesm` (Proxmox VE Storage Manager)
Gère les pools de stockage, l'allocation de volumes et les répertoires.

*   **Voir le statut des pools de stockage :**
    ```bash
    pvesm status
    ```
   
*   **Créer un nouveau pool (basé sur un répertoire) :**
    ```bash
    pvesm create dir new-datastore1 --path /mnt/storage-name --content images,iso
    ```
   

## 4. `pveum` (Proxmox VE User Management)
Gère les utilisateurs, les groupes, les rôles et les permissions (ACL).

*   **Ajouter un utilisateur :**
    ```bash
    pveum useradd user2@pve --password UserSecretPassword111 --comment "user2 – admin group" --groups admin
    ```
   
*   **Ajouter un rôle et définir des privilèges :**
    ```bash
    pveum roleadd vmmanager --privs VM.PowerMgmt,VM.Config.CDROM
    ```
   

## 5. `pvesh` (Proxmox API Shell)
Permet d'interagir directement avec l'API REST de Proxmox en ligne de commande.

*   **Lister les ressources du cluster :**
    ```bash
    pvesh ls /cluster/resources
    ```
   
*   **Créer une ressource (ex: nouvelle VM) :**
    ```bash
    pvesh create /nodes/pve-node1/qemu --vmid 106 --name new-vm-name --memory 2048 --cores 2
    ```
   

## 6. `pvecm` (Proxmox VE Cluster Manager)
Gère la création et la configuration des clusters, permettant la haute disponibilité et la migration à chaud.

*   **Créer un cluster (à exécuter sur le nœud maître) :**
    ```bash
    pvecm create cluster01
    ```
   
*   **Ajouter un nœud au cluster :**
    ```bash
    pvecm add 192.168.101.121
    ```
   

## 7. `hamanager` (High Availability Manager)
Configure et surveille les ressources de Haute Disponibilité (HA).

*   **Ajouter une VM à la Haute Disponibilité :**
    ```bash
    ha-manager add 105 --max-restarts 3 --max-migrate-tries 1
    ```
    *(Tente 3 redémarrages et 1 migration en cas de panne du nœud)*
*   **Migrer manuellement une VM HA :**
    ```bash
    ha-manager migrate 106 pve-node2
    ```
   

## 8. `vzdump`
Crée des sauvegardes (snapshots, suspend, stop) pour les VMs et les conteneurs.

*   **Sauvegarder une VM avec compression :**
    ```bash
    vzdump 101 --storage local --compress gzip --maxfiles 3
    ```
    *(Sauvegarde la VM 101 en la compressant avec gzip et conserve les 3 dernières sauvegardes)*
*   **Sauvegarder toutes les VMs en mode instantané :**
    ```bash
    vzdump --all --mode snapshot --storage nfs-backup --bwlimit 20480 --remove old --maxfiles 7
    ```
   

## 9. `qmrestore`
Restaure les machines virtuelles à partir d'une sauvegarde générée par `vzdump`.

*   **Restaurer sur l'ID d'origine (écrase la VM existante) :**
    ```bash
    qmrestore /var/lib/vz/dump/vzdump-qemu-101-2023_08_27-00_00_00.vma 101
    ```
   
*   **Restaurer comme nouvelle VM avec un nom spécifique :**
    ```bash
    qmrestore /mnt/pve/nfs-backup/dump/vzdump-qemu-101-2023_08_27-00_00_00.vma 103 --hostname restored-vm --name "MyRestoredVM"
    ```
   

## 10. `proxmox-backup-client`
Utilitaire pour interagir spécifiquement avec un Proxmox Backup Server (PBS).

*   **Effectuer une sauvegarde vers le serveur :**
    ```bash
    proxmox-backup-client backup etc.pxar /etc --repository root@pbs@10.10.10.101:datastore1
    ```
   
*   **Restaurer depuis le serveur :**
    ```bash
    proxmox-backup-client restore etc.pxar /restore/etc --repository root@pbs@10.10.10.101:datastore1
    ```
   

---


# Guide Complet des Commandes CLI Proxmox Essentielles (Version 2)

Ce document regroupe l'intégralité des commandes CLI spécifiques à Proxmox (QEMU/KVM, pare-feu, stockage, utilisateurs, API, cluster, haute disponibilité, sauvegardes et restaurations).

## 1. `qm` (Gestionnaire QEMU pour les VMs)
Cette commande permet d'interagir avec les machines virtuelles (VM) basées sur QEMU/KVM.

*   **Lister les VMs** (statut et ID) :
    ```bash
    qm list
    ```
*   **Créer une nouvelle machine virtuelle** (ex: ID 103, Debian, 2Go RAM, 2 cœurs) :
    ```bash
    qm create 103 --name "DebianVM" --memory 2048 --net0 virtio,bridge=vmbr0 --sockets 1 --cores 2 --ostype l26
    ```
*   **Attacher un disque à une VM** (ex: 32 Go sur SCSI) :
    ```bash
    qm set 105 --scsi0 local-lvm:32G
    ```
*   **Attacher un CD-ROM pour installer un OS** :
    ```bash
    qm set 105 --ide2 local:iso/debian-10.7.0-amd64-netinst.iso,media=cdrom
    ```
*   **Configurer l'ordre d'amorçage (Boot order)** :
    ```bash
    qm set 105 --boot order=ide2;scsi0
    ```
*   **Démarrer une VM** :
    ```bash
    qm start 103
    ```
*   **Arrêter une VM (Arrêt forcé / immédiat)** :
    ```bash
    qm stop 103
    ```
*   **Arrêter une VM (Arrêt propre / graceful shutdown)** :
    ```bash
    qm shutdown 101
    ```
*   **Migrer une VM vers un autre nœud** :
    ```bash
    qm migrate 103 node2
    ```
*   **Prendre un instantané (Snapshot) d'une VM** :
    ```bash
    qm snapshot 103 "before_upgrade"
    ```
*   **Restaurer l'état d'une VM à partir d'un instantané** :
    ```bash
    qm rollback 103 "before_upgrade"
    ```
*   **Cloner une machine virtuelle** (clone complet) :
    ```bash
    qm clone 103 104 --name "DebianClone" --full
    ```
*   **Redimensionner le disque d'une VM** (ex: ajouter 10 Go) :
    ```bash
    qm resize 103 scsi0 +10G
    ```

## 2. `pve-firewall` (Gestion du pare-feu)
Permet de configurer les règles du pare-feu pour le cluster, les nœuds, les VMs et les conteneurs.

*   **Vérifier le statut du pare-feu** :
    ```bash
    pve-firewall status
    ```
*   **Démarrer le service pare-feu** :
    ```bash
    pve-firewall start
    ```
*   **Recharger la configuration du pare-feu (sans l'arrêter)** :
    ```bash
    pve-firewall reload
    ```
*   **Créer une règle pour accepter le trafic SSH** :
    ```bash
    pve-firewall create rule -action accept -macro ssh
    ```
*   **Supprimer une règle spécifique** (remplacer `<rule-id>`) :
    ```bash
    pve-firewall delete rule <rule-id>
    ```
*   **Afficher le journal (log) du pare-feu** :
    ```bash
    pve-firewall log
    ```
*   **Créer une règle pour refuser (drop) le trafic HTTP** :
    ```bash
    pve-firewall create rule -action drop -macro http
    ```

## 3. `pvesm` (Gestionnaire de stockage)
Outil de gestion des pools, des volumes et des types de contenu.

*   **Lister le contenu d'un stockage spécifique** (remplacer `<storage>`) :
    ```bash
    pvesm list <storage>
    ```
*   **Vérifier le statut de tous les pools de stockage** :
    ```bash
    pvesm status
    ```
*   **Créer un nouveau pool de stockage basé sur un répertoire** :
    ```bash
    pvesm create dir new-datastore1 --path /mnt/storage-name --content images,iso
    ```
*   **Ajouter un backend de stockage NFS existant** :
    ```bash
    pvesm add nfs test-nfs-storage --server 192.168.101.100 --export /export/data --path /mnt/pve/test-nfs-storage --content images,iso
    ```
*   **Modifier la configuration d'un pool existant** (ex: autoriser les backups) :
    ```bash
    pvesm set local-storage01 --content images,iso,backup
    ```
*   **Allouer un nouveau volume pour une VM** (ex: 10 Go sur le stockage local) :
    ```bash
    pvesm alloc local-storage-name 100 10G
    ```

## 4. `pveum` (Gestion des utilisateurs et rôles)
Gère l'authentification, les utilisateurs, groupes, rôles et listes de contrôle d'accès (ACL).

*   **Ajouter un nouvel utilisateur** :
    ```bash
    pveum useradd user2@pve --password UserSecretPassword111 --comment "user2 – admin group" --groups admin
    ```
*   **Supprimer un utilisateur** :
    ```bash
    pveum userdel user3@pve
    ```
*   **Créer un groupe** :
    ```bash
    pveum groupadd support --comment "Support Team Group"
    ```
*   **Supprimer un groupe** :
    ```bash
    pveum groupdel guests
    ```
*   **Ajouter un rôle avec des privilèges spécifiques** :
    ```bash
    pveum roleadd vmmanager --privs VM.PowerMgmt,VM.Config.CDROM
    ```
*   **Modifier un rôle existant** (ex: ajouter un privilège) :
    ```bash
    pveum rolemod vmmanager --privs +VM.Config.Network
    ```
*   **Modifier les ACL (attribuer un rôle à un utilisateur sur une VM)** :
    ```bash
    pveum aclmod /vms/104 --roles vmmanager --users user4@pve
    ```
*   **Lister les domaines d'authentification** :
    ```bash
    pveum realm list
    ```
*   **Lister tous les utilisateurs** :
    ```bash
    pveum user list
    ```
*   **Afficher l'aide de la commande `pveum`** :
    ```bash
    pveum help
    ```

## 5. `pvesh` (Shell pour l'API REST)
Permet d'exécuter des requêtes vers l'API REST Proxmox directement en ligne de commande.

*   **Lister les ressources du cluster** :
    ```bash
    pvesh ls /cluster/resources
    ```
*   **Récupérer le statut d'un nœud spécifique** :
    ```bash
    pvesh get /nodes/pve-node1/status
    ```
*   **Modifier une configuration via l'API** (ex: renommer la VM 100) :
    ```bash
    pvesh set /nodes/pve-node1/qemu/100/config --name new-vm-name
    ```
*   **Créer une ressource via l'API** (ex: nouvelle VM) :
    ```bash
    pvesh create /nodes/pve-node1/qemu --vmid 106 --name new-vm-name --memory 2048 --cores 2
    ```
*   **Démarrer une VM spécifique via l'API** :
    ```bash
    pvesh start /nodes/pve-node1/qemu/101
    ```
*   **Arrêter proprement une VM via l'API** :
    ```bash
    pvesh shutdown /nodes/pve-node1/qemu/101
    ```
*   **Démarrer toutes les VMs d'un nœud** (remplacer `<nodename>`) :
    ```bash
    pvesh startall /nodes/<nodename>
    ```
*   **Arrêter toutes les VMs d'un nœud** :
    ```bash
    pvesh stopall /nodes/<nodename>
    ```

## 6. `pvecm` (Gestionnaire de Cluster)
Sert à créer un cluster, rejoindre des nœuds et surveiller le quorum.

*   **Voir le manuel pour toutes les commandes `pvecm`** :
    ```bash
    man pvecm
    ```
*   **Créer un nouveau cluster** (à exécuter sur le nœud maître) :
    ```bash
    pvecm create cluster01
    ```
*   **Ajouter le nœud actuel à un cluster existant** :
    ```bash
    pvecm add 192.168.101.121
    ```
*   **Supprimer un nœud du cluster** :
    ```bash
    pvecm delnode pve-node2
    ```
*   **Lister tous les nœuds du cluster** :
    ```bash
    pvecm nodes
    ```
*   **Définir un nouveau nœud maître** (remplacer `<nodename>`) :
    ```bash
    pvecm setmaster <nodename>
    ```
*   **Afficher le statut du cluster** (quorum, nombre de nœuds) :
    ```bash
    pvecm status
    ```
*   **Définir manuellement le nombre de nœuds attendu pour le quorum** :
    ```bash
    pvecm expected <number>
    ```

## 7. `ha-manager` (Gestionnaire de Haute Disponibilité)
Configure le comportement des VMs si un nœud tombe en panne.

*   **Afficher le statut de la Haute Disponibilité (HA)** :
    ```bash
    ha-manager status
    ```
*   **Activer la HA pour une VM avec paramètres de redémarrage et migration** :
    ```bash
    ha-manager add 105 --max-restarts 3 --max-migrate-tries 1
    ```
*   **Désactiver la HA et retirer la VM du gestionnaire** :
    ```bash
    ha-manager remove 105
    ```
*   **Migrer manuellement une VM HA vers un autre nœud** :
    ```bash
    ha-manager migrate 106 pve-node2
    ```

## 8. `vzdump` (Création de sauvegardes)
Outil natif de création de sauvegardes (snapshots) pour VMs et conteneurs.

*   **Sauvegarder plusieurs VMs séquentiellement** :
    ```bash
    vzdump 101 102 103
    ```
*   **Sauvegarder une VM avec compression gzip (conserver les 3 dernières)** :
    ```bash
    vzdump 101 --storage local --compress gzip --maxfiles 3
    ```
*   **Sauvegarder une VM en excluant certains dossiers (ex: les journaux)** :
    ```bash
    vzdump 102 --exclude-path /var/log
    ```
*   **Sauvegarder et purger les vieilles archives sur un stockage NFS** :
    ```bash
    vzdump 101 --storage nfs-backup --maxfiles 5 --remove old
    ```
*   **Sauvegarder toutes les VMs en mode snapshot avec limite de bande passante** (20 Mbps) :
    ```bash
    vzdump --all --mode snapshot --storage nfs-backup --bwlimit 20480 --remove old --maxfiles 7
    ```

## 9. `qmrestore` (Restauration des sauvegardes)
Restaure les fichiers `.vma` générés par `vzdump` vers des VMs.

*   **Restaurer une VM sur son ID d'origine** (écrase la VM existante) :
    ```bash
    qmrestore /var/lib/vz/dump/vzdump-qemu-101-2023_08_27-00_00_00.vma 101
    ```
*   **Restaurer la sauvegarde sur une nouvelle VM et cibler un stockage spécifique** :
    ```bash
    qmrestore /mnt/pve/nfs-backup/dump/vzdump-qemu-101-2023_08_27-00_00_00.vma 102 --storage local-lvm
    ```
*   **Restaurer la sauvegarde et modifier le nom d'hôte ainsi que le nom de la VM** :
    ```bash
    qmrestore /mnt/pve/nfs-backup/dump/vzdump-qemu-101-2023_08_27-00_00_00.vma 103 --hostname restored-vm --name "MyRestoredVM"
    ```

## 10. `proxmox-backup-client` (Intégration Proxmox Backup Server)
Utilitaire pour effectuer des sauvegardes et restaurations avec un PBS distant.

*   **Sauvegarder un répertoire vers le Proxmox Backup Server** :
    ```bash
    proxmox-backup-client backup etc.pxar /etc --repository root@pbs@10.10.10.101:datastore1
    ```
*   **Restaurer une archive depuis le serveur vers un répertoire local** :
    ```bash
    proxmox-backup-client restore etc.pxar /restore/etc --repository root@pbs@10.10.10.101:datastore1
    ```
***
