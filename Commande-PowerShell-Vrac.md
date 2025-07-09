
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
