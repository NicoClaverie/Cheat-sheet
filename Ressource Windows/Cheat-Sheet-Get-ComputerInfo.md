# 🧩 Cheat-Sheet PowerShell --- `Get-ComputerInfo`

## 🔍 Commande de base

``` 
Get-ComputerInfo
```

Affiche toutes les infos système disponibles sur la machine.

## 🎯 Obtenir une propriété spécifique

``` 
Get-ComputerInfo -Property <NomPropriété>
```

## 🔎 Rechercher des propriétés par motif

``` 
Get-ComputerInfo -Property "Os*"
Get-ComputerInfo -Property "*Bios*"
```

# 📦 Propriétés utiles

## 🖥️ Système d'exploitation

| Description      | Propriété            |
|:----------------:|:--------------------:|
| Nom de Windows   | `OsName`             |
| Version          | `WindowsVersion`     |
| Édition          | `WindowsEditionId`   |
| Build            | `OsBuildNumber`      |
| Architecture     | `OsArchitecture`     |
| Installation     | `OsInstallDate`      |
| Dernier boot     | `CsLastBootUpTime`   |

## 🏭 Matériel

| Description     | Propriété                        |
|:---------------:|:--------------------------------:|
| Fabricant       | `CsManufacturer`                 |
| Modèle          | `CsModel`                        |
| CPU physiques   | `CsNumberOfProcessors`           |
| Threads         | `CsNumberOfLogicalProcessors`    |
| CPU             | `CsProcessors`                   |
| RAM             | `CsTotalPhysicalMemory`          |

## 🔐 BIOS

| Description       | Propriété            |
|:-----------------:|:--------------------:|
| Fabricant         | `BiosManufacturer`   |
| Version           | `BiosVersion`        |
| Numéro de série   | `BiosSerialNumber`   |
| Date release      | `BiosReleaseDate`    |

## 🌐 Réseau

| Description     | Propriété                       |
|:---------------:|:-------------------------------:|
| Domaine         | `CsDomain`                      |
| Rôle            | `CsDomainRole`                  |
| Cartes réseau   | `CsNetworkAdapters`             |
| MAC             | `CsNetworkAdapters.MacAddress`  |


# 🧰 Exemples

``` 
Get-ComputerInfo -Property OsName,WindowsVersion,OsBuildNumber,CsModel,CsManufacturer
```

``` 
Get-ComputerInfo | Out-File "$env:USERPROFILE\Desktop\PC-Info.txt"
```

# 📝 Script PowerShell

``` 
# Script : Export des infos système Get-ComputerInfo
# Fichier : Export-ComputerInfo.ps1

$info = Get-ComputerInfo -Property `
    OsName,WindowsVersion,WindowsEditionId,OsBuildNumber,OsArchitecture,OsInstallDate,CsLastBootUpTime, `
    CsManufacturer,CsModel,CsNumberOfProcessors,CsNumberOfLogicalProcessors,CsTotalPhysicalMemory, `
    BiosManufacturer,BiosVersion,BiosSerialNumber,BiosReleaseDate, `
    CsDomain,CsDomainRole,PowershellVersion

$exportPath = "$env:USERPROFILE\Desktop\ComputerInfo.csv"

$info | Export-Csv -Path $exportPath -NoTypeInformation -Encoding UTF8

Write-Host "Fichier exporté vers : $exportPath" -ForegroundColor Green
```
