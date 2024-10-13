# Utilisation du mode ROMMON sur Cisco

## Qu'est-ce que le mode ROMMON ?
Le mode ROMMON (Read-Only Memory Monitor) est un mode utilisé pour la maintenance et le dépannage des équipements Cisco lorsque le routeur ou le commutateur ne peut pas démarrer correctement. Il s'agit d'une interface basique qui permet d'exécuter des commandes pour réparer ou reconfigurer le périphérique.

## Accès au mode ROMMON
Pour entrer dans le mode ROMMON, il suffit généralement d'interrompre le processus de démarrage en appuyant rapidement sur **Ctrl + Pause/Break** (selon le modèle) pendant l'initialisation de l'appareil.

## Commandes ROMMON

| **Commande** | **Description**                                                                                                                                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `confreg`    | Permet de modifier la configuration de l'enregistrement de démarrage (boot register). Utilisée pour changer l'ordre de démarrage ou forcer l'appareil à entrer en ROMMON lors du prochain démarrage. |
| `reset`      | Redémarre l'équipement à partir du mode ROMMON.                                                                                                                                                      |
| `tftpdnld`   | Télécharge une nouvelle image Cisco IOS via TFTP en mode ROMMON. Utilisée pour réinstaller ou mettre à jour l'IOS.                                                                                   |
| `xmodem`     | Télécharge une image IOS via le protocole XMODEM. Très utile lorsque TFTP n'est pas disponible.                                                                                                      |
| `boot`       | Démarre l'équipement en utilisant une image spécifique à partir de la mémoire flash.                                                                                                                 |
| `set`        | Affiche les variables d'environnement définies dans le mode ROMMON.                                                                                                                                  |
| `unset`      | Supprime une variable d'environnement définie dans le mode ROMMON.                                                                                                                                   |
| `dir`        | Affiche le contenu d'un répertoire, généralement utilisé pour voir les fichiers présents sur la mémoire flash.                                                                                       |
| `help`       | Affiche l'aide pour les commandes disponibles dans le mode ROMMON.                                                                                                                                   |

## Utilisation du mode ROMMON pour récupérer un équipement

### Changer le registre de configuration
L'enregistrement de démarrage (boot register) détermine comment le routeur va démarrer. Pour forcer l'appareil à démarrer en mode ROMMON, il faut modifier ce registre.

```
rommon 1 > confreg 0x2142
rommon 2 > reset
```

Le routeur redémarrera en ignorant la configuration enregistrée (ceci est utilisé pour récupérer des mots de passe oubliés).

### Téléchargement d'une nouvelle image IOS avec TFTP
Pour télécharger une nouvelle image IOS sur le routeur à partir du mode ROMMON, configurez d'abord les variables d'environnement nécessaires.

```
rommon 1 > IP_ADDRESS=192.168.1.10   # Adresse IP du routeur
rommon 2 > IP_SUBNET_MASK=255.255.255.0   # Masque de sous-réseau
rommon 3 > DEFAULT_GATEWAY=192.168.1.1    # Passerelle par défaut
rommon 4 > TFTP_SERVER=192.168.1.20       # Adresse IP du serveur TFTP
rommon 5 > TFTP_FILE=c2800nm-adventerprisek9-mz.124-25.bin  # Nom de l'image à télécharger
rommon 6 > tftpdnld
```

Cette commande télécharge l'image spécifiée depuis le serveur TFTP.

### Démarrage manuel d'une image IOS
Si l'image IOS est présente dans la mémoire flash, mais que le routeur ne démarre pas correctement, vous pouvez utiliser la commande `boot` pour démarrer l'image manuellement :

```
rommon 1 > boot flash:c2800nm-adventerprisek9-mz.124-25.bin
```

### Téléchargement via XMODEM
Lorsque TFTP n'est pas une option, vous pouvez utiliser `xmodem` pour télécharger une image IOS via une connexion série.

1. Connectez-vous à l'appareil via le port console.
2. Entrez la commande suivante dans le mode ROMMON pour lancer le transfert :

```
rommon 1 > xmodem -c c2800nm-adventerprisek9-mz.124-25.bin
```

3. Utilisez un programme comme **HyperTerminal** ou **TeraTerm** pour envoyer le fichier via XMODEM.

## Récupération d'un mot de passe Cisco

1. Accédez au mode ROMMON en interrompant le démarrage.
2. Modifiez le registre de démarrage pour ignorer la configuration enregistrée :

```
rommon 1 > confreg 0x2142
rommon 2 > reset
```

3. Une fois le routeur démarré, entrez en mode de configuration :

```
Router> enable
Router# configure terminal
Router(config)# enable secret <new-password>
```

4. Sauvegardez la configuration et rétablissez le registre de démarrage par défaut :

```
Router(config)# config-register 0x2102
Router(config)# end
Router# write memory
```

5. Redémarrez le routeur.

```
Router# reload
```

## Conclusion
Le mode ROMMON est une fonctionnalité essentielle pour la récupération, le dépannage et la maintenance d'équipements Cisco. Il permet de contourner certains problèmes graves, comme la perte de mot de passe ou la corruption de l'image IOS.
