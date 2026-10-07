# 📌 DISM Cheat Sheet (Windows)

Outil : DISM = Deployment Image Servicing and Management  
Utilisation : vérification et réparation de l'image système Windows

---

## 🔍 Vérifier l'intégrité de l'image

```
DISM /Online /Cleanup-Image /CheckHealth
```

- Vérifie si l'image est marquée comme endommagée
- Très rapide (ne fait pas de réparation)

---

## 🛠️ Scanner l'image pour détecter les corruptions

```
DISM /Online /Cleanup-Image /ScanHealth
```

- Analyse en profondeur (peut prendre quelques minutes)
- Ne répare pas, mais identifie les fichiers endommagés

---

## 🧹 Réparer l'image automatiquement (avec Windows Update)

```
DISM /Online /Cleanup-Image /RestoreHealth
```

- Tente une réparation via Windows Update
- Peut échouer si l'accès à internet est bloqué ou restreint

---

## 💾 Réparer avec une source locale (ISO monté, fichier WIM/ESD)

```
DISM /Online /Cleanup-Image /RestoreHealth /Source:D:\sources\install.wim /LimitAccess
```

- `D:` = lettre du lecteur contenant l'image
- `install.wim` ou `install.esd` doit contenir l’édition de Windows correspondante
- `/LimitAccess` = évite de contacter Windows Update

---

## 🧩 Identifier l'index correct dans install.wim / install.esd

```
DISM /Get-WimInfo /WimFile:D:\sources\install.wim
```

- Affiche la liste des éditions disponibles (Pro, Home, etc.)
- Ajoute `/Index:3` par exemple si besoin :

```
DISM /Online /Cleanup-Image /RestoreHealth /Source:D:\sources\install.wim:3 /LimitAccess
```

---

## 🔄 Réparer une partition Windows hors-ligne (WinRE)

```
DISM /Image:D:\ /Cleanup-Image /RestoreHealth /Source:E:\sources\install.wim /LimitAccess
```

- `D:` = lettre de la partition Windows
- `E:` = lecteur avec l’image source (clé USB ou ISO)
- Ajoute `/Index:X` si nécessaire (voir Get-WimInfo)

---

## 🧪 Autres commandes utiles

### Voir la version de l'image

```
DISM /Online /Get-CurrentEdition
```

### Lister toutes les éditions disponibles dans un WIM

```
DISM /Get-WimInfo /WimFile:E:\sources\install.wim
```

---

## Diagnostiquer et réparer 

Vérifiez l'intégrité de l'image. Montez votre fichier install.wim et utilisez DISM pour vérifier son état de santé.

1. Monter l'image
```
Dism /Mount-Image /ImageFile:"C:\chemin\vers\votre\install.wim" /Index:1 /MountDir:C:\Mount
```
2. Vérifiez la santé de l'image montée
```
Dism /Image:C:\Mount /Cleanup-Image /ScanHealth
```
3. Si des problèmes sont trouvés, tentez une réparation
```
Dism /Image:C:\Mount /Cleanup-Image /RestoreHealth
```
4. Démontez et sauvegardez les changements
```
Dism /Unmount-Image /MountDir:C:\Mount /Commit
```
5. Démontez et annuler les changements
```
Dism /Unmount-Image /MountDir:C:\Mount /Discard
```
---

## Mettre a jour l'image 

1. Monter l'image
```
Dism /Mount-Image /ImageFile:"C:\chemin\vers\votre\install.wim" /Index:1 /MountDir:"C:\mount"
```
2. Mettre a jour
```
Dism /Add-Package /Image:"C:\mount" /PackagePath:"C:\chemin\vers\miseajour.msu"
```
3. Démonter l'image
```
Dism /Unmount-Image /MountDir:"C:\mount" /Commit
```

---
## 🛑 Astuces

- `Online` = système en cours d’exécution
- `Image:D:\` = système hors-ligne (ex: depuis WinRE)
- Toujours vérifier l’espace disque libre
- Pour éviter les erreurs, désactiver l’antivirus le temps de la commande

---

## ⚙️ Gestion des fonctionnalités Windows (Windows Features)

DISM permet d'activer, désactiver, lister et obtenir des informations sur les fonctionnalités facultatives de Windows (Hyper-V, Sandbox, WSL, Services d'impression, etc.).

> ⚠️ **Note :** Toutes ces commandes doivent être exécutées dans une invite de commandes ou PowerShell **en tant qu'administrateur**.

---

### 1. 📋 Lister les fonctionnalités

* **Lister toutes les fonctionnalités disponibles et leur état :**
  ```cmd
  dism /Online /Get-Features
  ```

* **Filtrer pour afficher uniquement les fonctionnalités activées (PowerShell) :**
  ```powershell
  dism /Online /Get-Features | findstr /i "Enabled"
  ```

* **Filtrer pour afficher uniquement les fonctionnalités désactivées (PowerShell) :**
  ```powershell
  dism /Online /Get-Features | findstr /i "Disabled"
  ```

---

### 2. 🔍 Obtenir des informations sur une fonctionnalité

Pour connaître la description et le statut d'une fonctionnalité spécifique avant de l'activer ou de la désactiver :

```cmd
dism /Online /Get-FeatureInfo /FeatureName:NomDeLaFeature
```
*Exemple :*
```cmd
dism /Online /Get-FeatureInfo /FeatureName:Printing-PrintToPDFServices-Features
```

---

### 3. ❌ Désactiver une fonctionnalité

* **Désactiver une fonctionnalité spécifique :**
  ```cmd
  dism /Online /Disable-Feature /FeatureName:NomDeLaFeature
  ```

* **Exemples pratiques :**
  * Désactiver l'impression en PDF :
    ```cmd
    dism /Online /Disable-Feature /FeatureName:Printing-PrintToPDFServices-Features
    ```
  * Désactiver Internet Explorer 11 (si présent) :
    ```cmd
    dism /Online /Disable-Feature /FeatureName:Internet-Explorer-Optional-amd64
    ```
  * Désactiver le protocole obsolète SMBv1 (Recommandé pour la sécurité) :
    ```cmd
    dism /Online /Disable-Feature /FeatureName:SMB1Protocol
    ```

---

### 4. ✅ Activer une fonctionnalité

* **Activer une fonctionnalité simple :**
  ```cmd
  dism /Online /Enable-Feature /FeatureName:NomDeLaFeature /All
  ```
  *(L'argument `/All` permet d'activer également toutes les dépendances requises par la fonctionnalité).*

* **Exemples pratiques :**
  * Activer le Bac à sable Windows (Windows Sandbox) :
    ```cmd
    dism /Online /Enable-Feature /FeatureName:Containers-DisposableClientVM /All
    ```
  * Activer Hyper-V :
    ```cmd
    dism /Online /Enable-Feature /FeatureName:Microsoft-Hyper-V-All /All
    ```
  * Activer la plateforme de machine virtuelle (nécessaire pour WSL2) :
    ```cmd
    dism /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /All
    ```
  * Activer le sous-système Windows pour Linux (WSL1) :
    ```cmd
    dism /Online /Enable-Feature /FeatureName:Microsoft-Windows-Subsystem-Linux /All
    ```

---

### 💡 Astuces Utiles

1. **Éviter le redémarrage automatique :**
   Si vous enchaînez plusieurs commandes et ne voulez pas que Windows demande de redémarrer à chaque fois, ajoutez l'argument `/NoRestart` à la fin :
   ```cmd
   dism /Online /Enable-Feature /FeatureName:VirtualMachinePlatform /All /NoRestart
   ```

2. **Utiliser une source d'installation distante ou locale :**
   Si les fichiers d'une fonctionnalité sont manquants sur le système, vous pouvez pointer vers un fichier `install.wim` ou `ISO` Windows monté :
   ```cmd
   dism /Online /Enable-Feature /FeatureName:NetFx3 /All /Source:D:\sources\sxs /LimitAccess
   ```
   *(Exemple très courant pour installer .NET Framework 3.5 sans connexion Internet).*
