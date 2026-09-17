# 🧹 Cheat Sheet — Nettoyage et récupération d’espace sur C:

> Commandes Windows 10/11 — principalement PowerShell / CMD.
>
> ⚠️ Les commandes qui suppriment des fichiers doivent être exécutées avec **PowerShell en administrateur**.

## 🚀 Nettoyage rapide

| Objectif | Commande | Shell | Admin |
|---|---|---|---|
| Nettoyage automatique Windows | `cleanmgr /verylowdisk` | CMD / PowerShell | ✅ |
| Ouvrir le nettoyage de disque avec choix | `cleanmgr /sageset:1` | CMD / PowerShell | ✅ |
| Exécuter un nettoyage configuré | `cleanmgr /sagerun:1` | CMD / PowerShell | ✅ |

### ⭐ Commande rapide recommandée

```powershell
cleanmgr /verylowdisk
```

---

## 🗑️ Fichiers temporaires

| Cible | Commande | Risque |
|---|---|---|
| TEMP utilisateur | `Remove-Item "$env:TEMP\*" -Recurse -Force -ErrorAction SilentlyContinue` | Faible |
| TEMP Windows | `Remove-Item "C:\Windows\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue` | Faible |
| Vider les deux | Voir le bloc ci-dessous | Faible |

### Nettoyer les fichiers temporaires

```powershell
Remove-Item "$env:TEMP\*" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item "C:\Windows\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue
```

> Certains fichiers seront impossibles à supprimer parce qu'ils sont actuellement utilisés : c'est normal.

---

## 🔄 Cache Windows Update

Le dossier `SoftwareDistribution\Download` contient des fichiers téléchargés par Windows Update qui peuvent parfois prendre beaucoup de place.

```powershell
Stop-Service wuauserv -Force
Remove-Item "C:\Windows\SoftwareDistribution\Download\*" -Recurse -Force -ErrorAction SilentlyContinue
Start-Service wuauserv
```

| Étape | Commande |
|---|---|
| Arrêter Windows Update | `Stop-Service wuauserv -Force` |
| Nettoyer les téléchargements | `Remove-Item "C:\Windows\SoftwareDistribution\Download\*" -Recurse -Force -ErrorAction SilentlyContinue` |
| Redémarrer Windows Update | `Start-Service wuauserv` |

---

## 🧩 Nettoyage des composants Windows

### Nettoyage classique

```cmd
DISM /Online /Cleanup-Image /StartComponentCleanup
```

### Nettoyage plus agressif

```cmd
DISM /Online /Cleanup-Image /StartComponentCleanup /ResetBase
```

| Commande | Effet |
|---|---|
| `/StartComponentCleanup` | Supprime les anciennes versions de composants Windows devenues inutiles |
| `/ResetBase` | Nettoyage plus poussé de la base des composants |

> ⚠️ `/ResetBase` peut empêcher la désinstallation des anciennes mises à jour Windows. À utiliser seulement si tu veux vraiment récupérer davantage d'espace.

---

## 🔍 Trouver ce qui prend de la place

### Taille des dossiers directement sous C:

```powershell
Get-ChildItem C:\ -Directory -Force -ErrorAction SilentlyContinue |
ForEach-Object {
    [PSCustomObject]@{
        Dossier = $_.FullName
        TailleGB = [math]::Round(
            ((Get-ChildItem $_.FullName -Recurse -Force -File -ErrorAction SilentlyContinue |
            Measure-Object Length -Sum).Sum / 1GB), 2
        )
    }
} | Sort-Object TailleGB -Descending
```

### Les 20 plus gros fichiers de C:

```powershell
Get-ChildItem C:\ -File -Recurse -Force -ErrorAction SilentlyContinue |
Sort-Object Length -Descending |
Select-Object -First 20 FullName,@{N="TailleGB";E={[math]::Round($_.Length/1GB,2)}}
```

> ⚠️ Ces deux commandes peuvent prendre un certain temps sur un gros disque.

---

## 🧹 Corbeille

Vider la corbeille de tous les lecteurs :

```powershell
Clear-RecycleBin -Force -ErrorAction SilentlyContinue
```

---

## 💤 Hibernation

Si l'hibernation n'est pas utilisée, désactiver la fonction peut récupérer plusieurs Go.

```cmd
powercfg /h off
```

Pour la réactiver :

```cmd
powercfg /h on
```

> ⚠️ Cela désactive également le démarrage rapide sur certaines configurations Windows.

---

## 📦 Fichiers de vidage mémoire

Les fichiers `.dmp` peuvent devenir volumineux après des plantages.

### Chercher les dumps volumineux

```powershell
Get-ChildItem C:\ -Include *.dmp -File -Recurse -Force -ErrorAction SilentlyContinue |
Sort-Object Length -Descending |
Select-Object FullName,@{N="TailleGB";E={[math]::Round($_.Length/1GB,2)}}
```

> ⚠️ Ne supprime pas automatiquement les dumps : ils peuvent être utiles pour diagnostiquer un problème.

---

## 🧰 Nettoyage complet — bloc prêt à copier

À exécuter dans **PowerShell administrateur** :

```powershell
# 1. Fichiers temporaires utilisateur
Remove-Item "$env:TEMP\*" -Recurse -Force -ErrorAction SilentlyContinue

# 2. Fichiers temporaires Windows
Remove-Item "C:\Windows\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue

# 3. Cache Windows Update
Stop-Service wuauserv -Force
Remove-Item "C:\Windows\SoftwareDistribution\Download\*" -Recurse -Force -ErrorAction SilentlyContinue
Start-Service wuauserv

# 4. Corbeille
Clear-RecycleBin -Force -ErrorAction SilentlyContinue

# 5. Nettoyage des composants Windows
DISM /Online /Cleanup-Image /StartComponentCleanup
```

---

## 📊 Vérifier l'espace disponible

### PowerShell

```powershell
Get-PSDrive C
```

### Version lisible en Go

```powershell
$drive = Get-PSDrive C
"Libre : {0:N2} Go / {1:N2} Go" -f ($drive.Free/1GB), (($drive.Used+$drive.Free)/1GB)
```

### CMD

```cmd
wmic logicaldisk get caption,freespace,size
```

---

## 🛑 À éviter

| Action | Pourquoi |
|---|---|
| Supprimer manuellement `C:\Windows\WinSxS` | ❌ Peut casser Windows |
| Supprimer `C:\Windows\System32` | ❌ Critique |
| Supprimer tout `C:\Windows\Installer` | ❌ Peut casser les réparations/désinstallations |
| Supprimer tout `C:\ProgramData` | ❌ Données utilisées par les applications |
| Supprimer au hasard dans `AppData` | ⚠️ Certaines applications peuvent être affectées |

---

## 🥇 Ordre conseillé

| Priorité | Action | Commande |
|---:|---|---|
| 1 | Nettoyage Windows | `cleanmgr /verylowdisk` |
| 2 | TEMP utilisateur | `Remove-Item "$env:TEMP\*" ...` |
| 3 | TEMP Windows | `Remove-Item "C:\Windows\Temp\*" ...` |
| 4 | Cache Windows Update | `SoftwareDistribution\Download` |
| 5 | Composants Windows | `DISM /Online /Cleanup-Image /StartComponentCleanup` |
| 6 | Corbeille | `Clear-RecycleBin -Force` |
| 7 | Hibernation si inutile | `powercfg /h off` |
| 8 | Chercher les gros fichiers | `Get-ChildItem C:\ ...` |

---

## ⚡ TL;DR

Si tu veux juste récupérer rapidement de l'espace :

```powershell
cleanmgr /verylowdisk

Remove-Item "$env:TEMP\*" -Recurse -Force -ErrorAction SilentlyContinue
Remove-Item "C:\Windows\Temp\*" -Recurse -Force -ErrorAction SilentlyContinue

Stop-Service wuauserv -Force
Remove-Item "C:\Windows\SoftwareDistribution\Download\*" -Recurse -Force -ErrorAction SilentlyContinue
Start-Service wuauserv

Clear-RecycleBin -Force -ErrorAction SilentlyContinue

DISM /Online /Cleanup-Image /StartComponentCleanup
```
