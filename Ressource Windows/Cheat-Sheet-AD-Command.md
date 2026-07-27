# Cheat Sheet de commandes AD User et Computer

## 👤 Utilisateurs (Get-ADUser)

|Action|Commande PowerShell|
|:-:|:-:|
|Infos spécifiques + propriétés|`Get-ADUser -Identity "USER" -Properties logonWorkstations, lastLogonDate \| Select-Object SamAccountName, logonWorkstations, lastLogonDate`|
|Lister les groupes d'un user|`(Get-ADUser -Identity "USER" -Properties MemberOf).MemberOf`|
|Comptes verrouillés (Locked)|`Search-ADAccount -LockedOut \| Select-Object SamAccountName, Name`|
|Comptes désactivés|`Get-ADUser -Filter {Enabled -eq $false} \| Select-Object SamAccountName, Name`|
|Chercher par nom partiel|`Get-ADUser -Filter "Name -like '*USER*'" \| Select-Object SamAccountName, Name`|
|Chercher par email|`Get-ADUser -Filter "mail -like '*@domaine.com'" -Properties mail`|

## 💻 Ordinateurs (Get-ADComputer)

|Action|Commande PowerShell|
|:-:|:-:|
|Extraire le DN directement|`(Get-ADComputer -Identity "LAP0274").DistinguishedName`|
|Dernière connexion + OS|`Get-ADComputer -Identity "LAP0296" -Properties LastLogonDate, OperatingSystem | Select-Object Name, LastLogonDate, OperatingSystem`|
|Toutes les machines d'une OU|`Get-ADComputer -SearchBase "OU=Laptops,OU=Workstations,DC=domaine,DC=local" -Filter *`|
|Postes inactifs (+90 jours)|`Search-ADAccount -AccountInactive -TimeSpan 90.00:00:00 -ComputersOnly`|

## 👥 Groupes (Get-ADGroup / Get-ADGroupMember)

|Action|Commande PowerShell|
|:-:|:-:|
|Membres d'un groupe|`Get-ADGroupMember -Identity "G_Service_IT" \| Select-Object SamAccountName, Name, objectClass`|
|Membres (récursif avec sous-groupes)|`Get-ADGroupMember -Identity "G_DomainAdmins" -Recursive \| Select-Object SamAccountName, Name`|
|Ajouter un membre|`Add-ADGroupMember -Identity "G_Wifi_VPN" -Members "jdupont"`|
|Retirer un membre|`Remove-ADGroupMember -Identity "G_Wifi_VPN" -Members "jdupont"`|

## 🛠️ Modifs rapides & Utilitaires

|Action|Commande PowerShell|
|:-:|:-:|
|Déverrouiller un compte|`Unlock-ADAccount -Identity "jdupont"`|
|Réinitialiser un mot de passe (avec obligation de changer à la prochaine co)|`Set-ADAccountPassword -Identity "jdupont" -NewPassword (ConvertTo-SecureString "MotDePasse123!" -AsPlainText -Force) `ou` Set-ADUser -Identity "jdupont" -ChangePasswordAtLogon $true`|
|Modifier un attribut spécifique (ex: département ou poste)|`Set-ADUser -Identity "jdupont" -Department "Support IT" -Title "Technicien Systemes"`|
