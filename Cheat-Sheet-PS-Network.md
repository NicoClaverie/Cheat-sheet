# 10 commandes pour configurer le réseau sous Windows avec PowerShell


## Obtenir la liste des interfaces réseau

```Get-NetAdapter```

Cette commande est capable de lister les adaptateurs Ethernet (RJ45 et Wi-Fi), mais aussi les adaptateurs Bluetooth. La liste retournée contient un ensemble de propriétés correspondantes à des caractéristiques de chaque interface réseau (nom, statut, adresse MAC, vitesse de connexion, etc.).

Pour obtenir la liste de toutes les interfaces réseau actives, nous pouvons filtrer la liste de cette façon :

```Get-NetAdapter | Where-Object { $_.Status -eq "Up" }```


## Renommer une interface réseau

```Rename-NetAdapter -Name Ethernet0 -NewName LAN```

## Activer, désactiver ou redémarrer une interface réseau

Avec PowerShell, nous allons pouvoir activer ou désactiver une interface réseau, mais aussi redémarrer une interface réseau. Windows contient les trois cmdlets suivants prévus à cet effet :

- Enable-NetAdapter : pour activer une interface réseau
- Disable-NetAdapter : pour désactiver une interface réseau
- Restart-NetAdapter : pour redémarrer une interface réseau

Désactiver l'interface réseau

```Disable-NetAdapter -Name LAN```

Activer l'interface réseau

```Enable-NetAdapter -Name LAN```

Redémarrer l'interface réseau

```Restart-NetAdapter -Name LAN```

`LAN` peux etre remplacé par le nom de l'interface ciblé

Verifier si l'action est passé

```(Get-NetAdapter -Name LAN).Status```

## Obtenir la configuration IP d'une interface






https://www.it-connect.fr/chapitres/powershell-10-commandes-pour-configurer-le-reseau-sous-windows/
