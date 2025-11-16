# Guide des politiques d'exécution PowerShell

## 🔹 **Les différentes politiques d'exécution (**``**)**

Lorsque vous exécutez `Get-ExecutionPolicy`, PowerShell retourne l'une des valeurs suivantes :

| Politique        | Description                                                                                                     |
| ---------------- | --------------------------------------------------------------------------------------------------------------- |
| **Restricted**   | Par défaut sur Windows. Interdit l'exécution de scripts PowerShell, seule la saisie interactive est autorisée.  |
| **AllSigned**    | Autorise uniquement l'exécution de scripts signés par un éditeur de confiance.                                  |
| **RemoteSigned** | Autorise les scripts locaux non signés, mais exige une signature pour les scripts téléchargés.                  |
| **Unrestricted** | Autorise l'exécution de tous les scripts sans restriction (affiche un avertissement pour les scripts distants). |
| **Bypass**       | Désactive totalement la politique de restriction, aucun avertissement ni restriction.                           |
| **Undefined**    | Aucune politique définie, ce qui signifie que la restriction par défaut (`Restricted`) s'applique.              |

---

## 🔹 **Modifier la politique d'exécution avec **``

Vous pouvez changer la politique d'exécution avec la commande suivante :

```powershell
Set-ExecutionPolicy <PolicyName> -Scope <Scope> -Force
```

### 📉 **Les différentes options du paramètre **``

| Scope             | Description                                                                                                                 |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **MachinePolicy** | Défini via une GPO (ne peut pas être changé par un utilisateur).                                                            |
| **UserPolicy**    | Défini via une GPO pour un utilisateur spécifique.                                                                          |
| **Process**       | Applique la politique uniquement à la session PowerShell en cours. Elle est réinitialisée après la fermeture de la fenêtre. |
| **CurrentUser**   | Applique la politique à l'utilisateur actuel uniquement.                                                                    |
| **LocalMachine**  | Définit la politique pour tous les utilisateurs sur la machine (nécessite les droits administrateurs).                      |

---

## 🔹 **Exemples d'utilisation**

### 1️⃣ **Vérifier la politique actuelle**

```powershell
Get-ExecutionPolicy
```

### 2️⃣ **Vérifier la politique sur tous les niveaux de scope**

```powershell
Get-ExecutionPolicy -List
```

### 3️⃣ **Définir la politique en **``** pour tous les utilisateurs**

```powershell
Set-ExecutionPolicy RemoteSigned -Scope LocalMachine -Force
```

### 4️⃣ **Définir la politique uniquement pour l'utilisateur actuel**

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
```

### 5️⃣ **Appliquer une politique temporaire (sans modifier la configuration globale)**

```powershell
PowerShell -ExecutionPolicy Bypass -File MonScript.ps1
```

### 6️⃣ **Réinitialiser la politique d'exécution**

```powershell
Set-ExecutionPolicy Undefined -Scope LocalMachine
```

---

## 🔹 **Exécution d'un script sans modifier la politique globale**

Si vous souhaitez simplement exécuter un script ponctuellement sans modifier la politique globale, utilisez :

```powershell
powershell -ExecutionPolicy Bypass -File "C:\chemin\vers\ton_script.ps1"
```

Cela permet d'exécuter un script sans avoir à modifier la politique d'exécution de manière permanente.

---

🔒 **Note de sécurité** : Modifier la politique d'exécution peut exposer votre système à des risques si vous exécutez des scripts non fiables. Il est recommandé de laisser la politique sur `RemoteSigned` ou `AllSigned` lorsque c'est possible.

##

Script en `.bat` pour changer la politique d'execution des scripts PowerShell

```batch
powershell -Command "Start-Process powershell -ArgumentList '-NoProfile -ExecutionPolicy Bypass -Command Set-ExecutionPolicy RemoteSigned -Force' -Verb runAs"
```