
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
