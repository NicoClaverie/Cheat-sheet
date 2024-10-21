# GPOZaurr - Résumé et Commandes de Base

## Qu'est-ce que GPOZaurr ?
GPOZaurr est un module PowerShell destiné à l'administration et à la gestion des objets de stratégie de groupe (GPO) dans les environnements Windows. Il aide les administrateurs à détecter les erreurs, à analyser les configurations et à corriger les problèmes courants liés aux GPOs.

GPOZaurr peut générer des rapports détaillés sur divers aspects comme :
- Liens brisés
- Permissions incorrectes
- Héritage bloqué
- Doublons de GPO
- Fichiers obsolètes dans SysVol

## Installation
Avant d'utiliser GPOZaurr, assurez-vous d'avoir les outils RSAT (Remote Server Administration Tools) installés :

```powershell
Add-WindowsCapability -Online -Name 'Rsat.GroupPolicy.Management.Tools~~~~0.0.1.0'
```

Ensuite, installez GPOZaurr avec la commande suivante :

```powershell
Install-Module -Name GPOZaurr -AllowClobber -Force
```

## Commandes de Base

### 1. **Invoke-GPOZaurr**
Cette commande est la plus utilisée. Elle permet de générer plusieurs rapports sur l'état des GPOs.

```powershell
Invoke-GPOZaurr
```
Cela inclut des rapports tels que :
- `GPOBroken` : Détecte les GPO cassés
- `GPOPermissions` : Vérifie les permissions des GPOs
- `GPOBlockedInheritance` : Identifie les héritages bloqués

### 2. **GPOList**
Liste tous les objets de stratégie de groupe disponibles dans votre domaine.

```powershell
Get-GPOZaurr -List
```

### 3. **GPOLinks**
Permet de voir où sont appliqués les GPOs dans l'Active Directory.

```powershell
Get-GPOZaurr -Links
```

### 4. **GPOOwners**
Vérifie les propriétaires actuels des GPOs.

```powershell
Get-GPOZaurr -Owners
```

## Mise à jour du module
Pour mettre à jour GPOZaurr :

```powershell
Update-Module -Name GPOZaurr
```

## Documentation
Pour plus de détails, consultez la page GitHub du projet : [GPOZaurr sur GitHub](https://github.com/EvotecIT/GPOZaurr)  
Lien vers un tutoriel IT-Connect : [GPOZaurr sur IT-Connect](https://www.it-connect.fr/gpozaurr-outil-ultime-pour-audit-analyser-gpo/)
Ce fichier Markdown résume les principales informations et quelques commandes utiles pour débuter avec GPOZaurr.
