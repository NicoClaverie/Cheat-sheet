# 🧠 Cheat Sheet – Variables d'environnement Windows (PowerShell)

## 🔹 Syntaxe PowerShell
Les variables d'environnement s'utilisent avec le préfixe `$Env:`  
Exemple : `$Env:USERNAME`

---

## 📋 Variables courantes

| Variable                    | Description                                                | Exemple d'utilisation                          |
|-----------------------------|------------------------------------------------------------|------------------------------------------------|
| `$Env:USERNAME`             | Nom de l'utilisateur connecté                              | `"Utilisateur : $Env:USERNAME"`               |
| `$Env:USERDOMAIN`           | Domaine ou nom de l'ordinateur local                       | `"Domaine : $Env:USERDOMAIN"`                 |
| `$Env:USERPROFILE`          | Dossier utilisateur (ex. `C:\Users\Jean`)                  | `cd $Env:USERPROFILE`                         |
| `$Env:HOMEPATH`             | Chemin relatif au profil utilisateur                       | `Join-Path $Env:HOMEDRIVE $Env:HOMEPATH`      |
| `$Env:HOMEDRIVE`            | Lettre du lecteur principal (ex. `C:`)                     |                                                |
| `$Env:COMPUTERNAME`         | Nom de l’ordinateur                                        | `"PC : $Env:COMPUTERNAME"`                    |
| `$Env:OS`                   | Système d’exploitation (souvent "Windows_NT")              |                                                |
| `$Env:PROCESSOR_ARCHITECTURE` | Architecture CPU (x86 / AMD64)                         |                                                |
| `$Env:NUMBER_OF_PROCESSORS`| Nombre de cœurs détectés                                   |                                                |
| `$Env:APPDATA`              | Dossier AppData (Roaming)                                  | `C:\Users\Jean\AppData\Roaming`               |
| `$Env:LOCALAPPDATA`         | Dossier AppData local                                      | `C:\Users\Jean\AppData\Local`                 |
| `$Env:TEMP` / `$Env:TMP`    | Dossier temporaire de l'utilisateur                        | `Get-ChildItem $Env:TEMP`                     |
| `$Env:ProgramFiles`         | Dossier Program Files (64 bits)                            |                                                |
| `$Env:ProgramFiles(x86)`    | Dossier Program Files (32 bits)                            |                                                |
| `$Env:SystemRoot`           | Dossier Windows (`C:\Windows`)                             |                                                |
| `$Env:Path`                 | Chemins d'exécutables disponibles                          | `$Env:Path -split ";"`                        |
| `$Env:WINDIR`               | Alias du dossier Windows                                   | Souvent identique à `$Env:SystemRoot`         |
| `$Env:LOGONSERVER`          | Contrôleur de domaine ayant authentifié l'utilisateur      | Utile en environnement AD                     |

---

## 🛠️ Exemples pratiques en PowerShell

```powershell
# Lister toutes les variables d'environnement
Get-ChildItem Env:

# Ajouter un chemin au PATH temporairement
$Env:Path += ";C:\MonOutil"

# Créer un fichier dans le dossier temporaire
New-Item "$Env:TEMP\test.txt" -ItemType File
