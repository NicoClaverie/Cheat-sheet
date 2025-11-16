# RSAT --- Explication complète (Version complète)

## 1) Qu'est-ce que RSAT ?

RSAT (*Remote Server Administration Tools*) est un ensemble d'outils
fournis par Microsoft permettant d'administrer **à distance** des rôles
et services Windows Server depuis un poste Windows (AD, DNS, DHCP, GPO,
etc.).

------------------------------------------------------------------------

## 2) Que contient RSAT ?

### A) Outils graphiques (MMC)

-   Active Directory Users and Computers (ADUC)
-   DNS Manager
-   DHCP Manager
-   Group Policy Management Console (GPMC)
-   Server Manager distant

### B) Modules PowerShell

-   Module *ActiveDirectory*
-   Module *DnsServer*
-   Outils DHCP
-   Cmdlets de gestion des GPO

### C) Outils CLI divers

-   `csvde`, `ldifde`
-   `dsquery`, `dsadd`, etc.

------------------------------------------------------------------------

## 3) Remarques importantes

-   RSAT est **intégré nativement** à Windows 10/11 (Feature on Demand).
-   Pas disponible sur **Windows Home**.
-   Souvent bloqué par **WSUS**, provoquant l'erreur `0x800f0954`.

------------------------------------------------------------------------

## 4) Commandes PowerShell utiles

### Lister tous les composants RSAT

``` powershell
Get-WindowsCapability -Online -Name "Rsat*" | Select-Object DisplayName, Name, State
```

### Installer un composant (ex : AD)

``` powershell
Add-WindowsCapability -Online -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
```

### Installer *tous* les outils RSAT

``` powershell
Get-WindowsCapability -Online -Name "Rsat*" | Add-WindowsCapability -Online
```

### Désinstaller un composant

``` powershell
Remove-WindowsCapability -Online -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
```

------------------------------------------------------------------------

## 5) Exemples concrets d'utilisation

### A) Utilisation d'ADUC

Ouvre **Windows Tools** → *Active Directory Users and Computers*.

### B) Exemple PowerShell (création d'un utilisateur AD)

``` powershell
Import-Module ActiveDirectory

New-ADUser `
 -Name "Jean Dupont" `
 -SamAccountName jdupont `
 -GivenName Jean `
 -Surname Dupont `
 -Enabled $true `
 -Path "OU=Utilisateurs,DC=exemple,DC=local" `
 -AccountPassword (ConvertTo-SecureString "P@ssw0rd!" -AsPlainText -Force)
```

### Lister les utilisateurs

``` powershell
Get-ADUser -Filter * | Select-Object Name, SamAccountName
```

### Réinitialiser un mot de passe

``` powershell
Set-ADAccountPassword jdupont -Reset -NewPassword (ConvertTo-SecureString "NouveauP@ss1" -AsPlainText -Force)
```

------------------------------------------------------------------------

## 6) DNS & DHCP

### DNS PowerShell (si module présent)

``` powershell
Get-DnsServerResourceRecord -ZoneName "exemple.local"
```

### Ajouter un enregistrement A

``` powershell
Add-DnsServerResourceRecordA -ZoneName "exemple.local" -Name "serveur1" -IPv4Address "192.168.1.50"
```

------------------------------------------------------------------------

## 7) Problèmes courants

### Erreur 0x800f0954 (WSUS)

Solutions : - Passer Windows Update en mode online - Installer via ISO
(`-Source`) - Demander au service IT de débloquer FOD

### RSAT disparaît après une mise à jour majeure

→ Il faut réinstaller les Features On Demand.

------------------------------------------------------------------------

## 8) Mini-tutoriel d'installation complète

``` powershell
Get-WindowsCapability -Online -Name "Rsat*" |
Where-Object {$_.State -eq "NotPresent"} |
Add-WindowsCapability -Online
```

### Vérifier l'installation :

``` powershell
Import-Module ActiveDirectory
Get-ADDomain
```

------------------------------------------------------------------------

## 9) Résumé rapide

-   RSAT = outils d'administration à distance pour Windows Server.
-   Intégré dans Windows 10/11.
-   Permet d'administrer AD, DNS, DHCP, GPO sans se connecter au
    serveur.
-   Très utile pour automatiser via PowerShell.

------------------------------------------------------------------------

Si tu veux une version PDF, DOCX ou même une version encore plus
détaillée, je peux aussi te les générer.
