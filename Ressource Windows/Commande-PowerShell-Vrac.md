
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

---
## Savoir a qui appartient un SID

```
$SID = "S-1-5-21-1125411162-415437191-1846952604-512"
$objSID = New-Object System.Security.Principal.SecurityIdentifier($SID)
$objUser = $objSID.Translate([System.Security.Principal.NTAccount])
Write-Host "Le propriétaire est : $($objUser.Value)"
```

---
## Lister les logiciels installés sur un PC

Cette commande permet de :
- Lister les logiciels installés
- Vérifier les versions
- Faciliter un audit ou un dépannage
- Gagner du temps en support utilisateur

```
Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\* |
Select DisplayName, DisplayVersion, Publisher |
Sort DisplayName 
```

Pour exporter la liste dans un fichier :
```
... | Export-Csv "C:\Temp\Software_List.csv" -NoTypeInformation
```

---

## Bout de script powershell pour aller chercher un fichier en mode fenetre 

```PowerShell
# --- DEBUT DU BLOC DE SELECTION ---
Add-Type -AssemblyName System.Windows.Forms

$Explorateur = New-Object System.Windows.Forms.OpenFileDialog -Property @{
    # Configuration du dossier de départ
    InitialDirectory = "C:\" 
    
    # Configuration des filtres (Nom|*.extension)
    Filter = "Tous les fichiers (*.*)|*.*"
    
    # Index du filtre sélectionné par défaut (ici le premier : *.*)
    FilterIndex = 1
    
    # Titre de la fenêtre
    Title = "Veuillez selectionner un fichier"
}

# Affiche la fenêtre et vérifie si l'utilisateur clique sur "Ouvrir"
if ($Explorateur.ShowDialog() -eq 'OK') {
    $FichierSelectionne = $Explorateur.FileName
} else {
    Write-Host "Selection annulee par l'utilisateur." -ForegroundColor Yellow
    return # Stoppe le script si pas de fichier
}
# --- FIN DU BLOC DE SELECTION ---

# Test de sortie pour vérifier que ça marche :
Write-Host "Le script va travailler sur : $FichierSelectionne" -ForegroundColor Cyan
```

### Modification possible du filtre de format :  

Le format du filtre fonctionne toujours par paires : `"Nom affiché|*.extension"`.  
Si tu veux mettre plusieurs extensions dans un seul choix, on utilise le point-virgule.  

Voici une liste de filtres courants que tu peux copier-coller selon tes besoins :  

1. Les classiques (Scripts et Data)
- Fichiers CSV uniquement :  
  `"Fichiers CSV (*.csv)|*.csv"`

- Scripts PowerShell :  
  `"Scripts PowerShell (*.ps1)|*.ps1"`

- Fichiers Texte et Logs :  
  `"Fichiers Texte et Log (*.txt; *.log)|*.txt;*.log"`

- Fichiers JSON / XML (Config) :  
  `"Fichiers de configuration (*.json; *.xml)|*.json;*.xml"`

2. Bureautique
- Fichiers Excel :  
  `"Tableaux Excel (*.xlsx; *.xls)|*.xlsx;*.xls"`

- Documents PDF :  
  `"Documents PDF (*.pdf)|*.pdf"`

3. Les "Combinés" (Plusieurs choix dans la liste déroulante)
Si tu veux offrir plusieurs options à l'utilisateur dans le menu déroulant de la fenêtre, il suffit de les enchaîner avec des barres verticales (pipes) `|`.

Le combo "Spécial Admin" :

```PowerShell
Filter = "Logs et Textes (*.log; *.txt)|*.log;*.txt|Scripts (*.ps1; *.bat; *.vbs)|*.ps1
```

### Ciblage de dossier spécifique

Voici les différentes options pour `InitialDirectory` :  

1. Chemins statiques (En dur)  

Utile si ton infrastructure est standardisée.  

- Dossier spécifique : `"C:\Temp\PingLogs"`
- Racine d'un disque : `"D:\"`
- Chemin réseau (UNC) : `"\\ServeurDeLogs\Partage\Archives"`

2. Dossiers Spéciaux Windows (Dynamiques)  

C'est la méthode la plus propre car elle s'adapte à chaque utilisateur (le Bureau n'a pas le même nom selon la session). On utilise la classe `[Environment]`.  

|Destination|Code à mettre dans InitialDirectory|
|:-|:-|
|Bureau|`[Environment]::GetFolderPath('Desktop')`|
|Documents|`[Environment]::GetFolderPath('MyDocuments')`|
|Téléchargements|`"$env:USERPROFILE\Downloads"`|
|Dossier Utilisateur|`"$env:USERPROFILE"`|
|Dossier Windows|`[Environment]::GetFolderPath('Windows')`|

3. Chemins relatifs au script  

Très pratique si tu distribues ton script à des collègues et que les logs sont dans un sous-dossier du script.

- Le dossier où se trouve le script :  
  `$PSScriptRoot`
- Un sous-dossier "Logs" situé à côté du script :  
  `Join-Path $PSScriptRoot "Logs"`
 
4. Variables d'environnement (Raccourcis)

PowerShell peut utiliser les variables système directement avec le préfixe `$env`:.

- Dossier temporaire de Windows :   
  `$env:TEMP`
- Dossier Program Files :  
  `$env:ProgramFiles`

Exemple de mise en pratique "Pro" :Voici comment je l'écrirais pour que ce soit robuste (il essaye un dossier précis, sinon il retombe sur ses pieds) :

```PowerShell
$dossierVise = "C:\Toto"

$Explorateur.InitialDirectory = if (Test-Path $dossierVise) { 
    $dossierVise 
} else { 
    [Environment]::GetFolderPath('Desktop') 
}
```
Petite astuce : Si tu mets un chemin qui n'existe pas et que tu n'as pas fait de vérification, Windows ouvrira la boîte de dialogue par défaut dans "Bureau".


---
