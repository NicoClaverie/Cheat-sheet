# Guide Robocopy : Copie, Sauvegarde et Synchronisation sous Windows 
(Généré avec ChatGPT)


## 🔹 Qu'est-ce que Robocopy ?
`Robocopy` (Robust File Copy) est un outil intégré à Windows permettant de copier, sauvegarder et synchroniser des fichiers et dossiers avec des fonctionnalités avancées.

Il est plus puissant que `copy` et `xcopy` et permet notamment :
- La reprise après interruption  
- La copie en mode miroir  
- La gestion des permissions et des attributs  

---

## 🔹 Syntaxe de base
La commande `Robocopy` s’utilise ainsi :  
```
robocopy [source] [destination] [options]
```
Exemple simple :  
```
robocopy C:\Source D:\Destination
```
👉 Copie tout le contenu de `C:\Source` vers `D:\Destination`.

---

## 🔹 Exemples courants
### 1. Synchroniser deux dossiers (mode miroir)
```
robocopy C:\Source D:\Destination /MIR
```
👉 Rend les deux dossiers identiques (supprime les fichiers absents de la source).

### 2. Copier uniquement certains fichiers
```
robocopy C:\Source D:\Destination *.docx
```
👉 Copie uniquement les fichiers `.docx`.

### 3. Exclure des fichiers ou dossiers
```
robocopy C:\Source D:\Destination /XF secret.txt /XD "Dossier caché"
```
👉 Exclut le fichier `secret.txt` et le dossier `"Dossier caché"`.

### 4. Conserver un journal des opérations
```
robocopy C:\Source D:\Destination /LOG:C:\Logs\robocopy_log.txt
```
👉 Sauvegarde les actions réalisées dans `robocopy_log.txt`.

### 5. Déplacer au lieu de copier
```
robocopy C:\Source D:\Destination /MOV
```
👉 Déplace les fichiers (sans les dossiers).  
```
robocopy C:\Source D:\Destination /MOVE
```
👉 Déplace fichiers **et** dossiers.

### 6. Copier en mode sauvegarde (contourner restrictions)
```
robocopy C:\Source D:\Destination /B
```
👉 Permet la copie même si des fichiers sont protégés.

---

## 🔹 Tableau récapitulatif des options principales

| Option  | Description |
|---------|------------|
| `/MIR`  | Synchronise les répertoires (supprime ce qui est absent de la source). |
| `/MOV`  | Déplace uniquement les fichiers. |
| `/MOVE` | Déplace fichiers **et** dossiers. |
| `/LOG:<fichier>` | Crée un fichier journal des actions effectuées. |
| `/XF <fichier>` | Exclut un ou plusieurs fichiers. |
| `/XD <dossier>` | Exclut un ou plusieurs dossiers. |
| `/B`    | Copie en mode sauvegarde (bypass certaines restrictions). |
| `/E`    | Copie les sous-dossiers, y compris les vides. |
| `/SEC`  | Copie les fichiers avec leurs permissions. |
| `/Z`    | Active le mode reprise en cas d’interruption. |


## 🔹 Tableau d'options particulierement utile

| Option  | Description |
|---------|------------|
| `/S`    | Copie les sous-répertoires sauf les répertoires vides. |
| `/E`    | Copie tous les sous-répertoires, y compris les vides. |
| `/MIR`  | Synchronise les répertoires (supprime ce qui est absent de la source). |
| `/SEC`  | Copie les permissions NTFS des fichiers et dossiers. |
| `/COPYALL` | Copie tous les attributs d’un fichier (date de création, de modification, etc.). |
| `/Z`    | Active la copie en mode redémarrable (reprend en cas d’interruption). |
| `/ZB`   | Utilise `/Z`, et passe en mode sauvegarde si l’accès est refusé. |
| `/R:5`  | Réessaie 5 fois en cas d’échec (valeur par défaut : 1 million). |
| `/W:5`  | Attente de 5 secondes entre chaque essai (par défaut 30 sec). |
| `/NP`   | N'affiche pas le pourcentage de progression. |
| `/V`    | Mode verbeux : affiche plus de détails, y compris les fichiers ignorés. |
| `/MT:16`| Active le mode multithread avec 16 threads (par défaut 8, max 128). |
| `/LOG:<fichier>` | Précise un fichier log pour enregistrer la sortie. |


---

## 🔹 Conclusion
Robocopy est un outil puissant pour gérer efficacement la copie et la synchronisation des fichiers sous Windows.  
Si tu veux plus d’options, tape :
```
robocopy /?
```

---

## Exemple pour sauvegarde et restauration d'une clé USB sur un lecteur réseau

### 1. Sauvegarde vers lecteur réseau et affichage du fichier de LOG

```
robocopy $PSScriptRoot "G:\Mon Drive\BackupCleUSB" /MIR /COPY:DAT /FFT /R:5 /W:2 /LOG:"G:\Mon Drive\BackupCleUSB\log_backup.txt"
Invoke-item -path "G:\Mon Drive\BackupCleUSB\log_backup.txt"
```

### 2. Restauration du lecteur réseau vers la clé en D:\ et affichage du LOG

```
robocopy "G:\Mon Drive\BackupCleUSB" D:\ /E /COPY:DAT /FFT /R:5 /W:2 /LOG:"G:\Mon Drive\BackupCleUSB\log_restore.txt"
invoke-item -path "G:\Mon Drive\BackupCleUSB\log_restore.txt"
```




Source : https://www.it-connect.fr/robocopy-copie-sauvegarde-et-synchronisation-de-donnees-sous-windows/
