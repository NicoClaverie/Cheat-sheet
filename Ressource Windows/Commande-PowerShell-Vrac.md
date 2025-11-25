
## Permet de créer un fichier `.key` contenant un texte crypté, pratique pour les mots de passe
```
Read-Host -AsSecureString | ConvertFrom-SecureString | Out-File -FilePath "C:\Chemin\De\Votre\Choix\password.key"
```

## Cette commande ne fonctionnera que sur l'ordinateur et avec le compte qui a créé le fichier
```
$securePassword = Get-Content -Path "C:\Chemin\De\Votre\Choix\password.key" | ConvertTo-SecureString
$credential = New-Object System.Management.Automation.PSCredential("nomdutilisateurfictif", $securePassword)
$credential.GetNetworkCredential().Password
```

---

## Bloc à ajouter pour une élévation de privilege d'un script
### --- Début du bloc d'auto-élévation ---
```
# Vérifie si la session actuelle a les droits d'administrateur
$currentUser = New-Object Security.Principal.WindowsPrincipal([Security.Principal.WindowsIdentity]::GetCurrent())
if (-not $currentUser.IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)) {
    # Si non, on relance le script actuel en demandant l'élévation
    $arguments = "& '" + $myinvocation.mycommand.definition + "'"
    Start-Process powershell.exe -Verb RunAs -ArgumentList $arguments
    # On quitte la session non-administrateur
    exit
}
```

### --- Fin du bloc d'auto-élévation ---
```
# Le reste de votre script, qui s'exécutera maintenant avec les droits admin, commence ici.
Write-Host "Le script s'exécute avec les privilèges d'administrateur."
# ... votre code ...
```

---

## Bloc pour ajouter une journalisation facile aux scripts

```
# Preparation de la journalisation
$LogFile = "C:\Windows\Temp\toto.log"

Function Write-Log {
    Param ([string]$LogString)
    $Stamp = (Get-Date).toString("yyyy-MM-dd HH:mm:ss")
    $LogMessage = "$Stamp $LogString"
    Add-content $LogFile -value $LogMessage
    Write-Host $LogString
}

# Debut du Script
Write-Log "Phrase aleatoire pour indiquer le debut du script"
```

---

## Astuce : Rendre un script Batch portable

Pour éviter les chemins "en dur" (ex: `C:\Dossier\fichier.exe`) et permettre à un script de fonctionner depuis n'importe quel emplacement, on utilise la variable `%~dp0`.

- **Qu'est-ce que c'est ?**
  `%~dp0` représente automatiquement le chemin complet du dossier contenant le script.

- **Comment l'utiliser ?**
  On le place devant le nom du fichier auquel on veut accéder.

### La variable `%~dp0`

La variable `%~dp0` est une variable magique dans les scripts batch. Elle est automatiquement remplacée par le **chemin complet du dossier où se trouve le script**.

- **`%~`** : Démarre une séquence d'expansion de variable.
- **`d`** : Représente la lettre du lecteur (ex: `C:`).
- **`p`** : Représente le chemin d'accès (ex: `\MonDossier\`).
- **`0`** : Fait référence au fichier script lui-même.

### Exemple concret

**Avant (chemin fixe) :**
```
:: Ne fonctionne que si le fichier est exactement ici
copy "D:\Installation\config.txt" "%APPDATA%\MonApp\"
```

Après (chemin portable) :
```
:: Fonctionne peu importe où se trouve le dossier du script
copy "%~dp0config.txt" "%APPDATA%\MonApp\"
```

**Règle d'or** : Toujours entourer le chemin de guillemets `"%~dp0fichier.exe"` pour que cela fonctionne même si le chemin contient des espaces.

---

## Déclencher une action 

```
# 1. Déclenchement de la question et capture de la réponse
$reponse = Read-Host "Voulez-vous exécuter cette action ? (O/N)"
$FunctionName = "Nom de la fonction

# 2. Vérification de la réponse
# On vérifie si la réponse est 'O' (Oui), en ignorant la casse (-clt = case-less equal, ou -match '^[oO] pour une expression régulière)
if ($reponse -match '^[oO]') {
    # Exécution de la fonction
    $FunctionName
} else {
    Write-Host "Action annulée ou réponse non reconnue." -ForegroundColor Yellow
}
```

---

## Commande pour créer un wrapper et aider a lancer un script powershell

```
powershell.exe -NonInteractive -ExecutionPolicy Bypass -File "%~dp0votre_script.ps1"
```
```
@echo off
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "%~dp0votre_script.ps1"
```

## Savoir a qui appartient un SID

```
$SID = "S-1-5-21-1125411162-415437191-1846952604-512"
$objSID = New-Object System.Security.Principal.SecurityIdentifier($SID)
$objUser = $objSID.Translate([System.Security.Principal.NTAccount])
Write-Host "Le propriétaire est : $($objUser.Value)"
```
