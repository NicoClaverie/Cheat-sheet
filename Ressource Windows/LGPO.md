# Guide d'utilisation de **LGPO.exe** (Local Group Policy Object Utility)

LGPO.exe est un outil Microsoft officiel permettant d'automatiser l'import, l'export et la gestion des stratégies locales Windows (GPO locales), sans passer par l'éditeur graphique.

---

## 📥 Installation et récupération de LGPO.exe
LGPO.exe fait partie du package **Microsoft Security Compliance Toolkit (SCT)**.

Téléchargement : Microsoft Security Compliance Toolkit (SCT)

Une fois extrait, l'exécutable se trouve généralement dans :
```
...\LGPO\LGPO.exe
```

---

## 🧩 Fonctionnalités principales
- Exporter les GPO locales actuelles.
- Importer des GPO depuis un dossier.
- Sauvegarder / restaurer les paramètres de sécurité (`secedit`), les modèles administratifs (`registry.pol`), et les préférences.
- Manipuler les modèles .ADMX.

---

## 📌 Syntaxe générale
```
LGPO.exe <commande> [options]
```

---

## 📤 Exporter les GPO locales
Permet de sauvegarder toutes les configurations locales dans un dossier.

```
LGPO.exe /b C:\SauvegardeGPO
```

Le dossier contiendra :
- `registry.pol` (User + Machine)
- `secedit.sdb` (stratégies de sécurité)
- `GroupPolicyPreferences` si présent
- ADMX copiés

---

## 📥 Importer des GPO locales
Applique une sauvegarde ou un modèle directement sur l'ordinateur.

```
LGPO.exe /g C:\MesGPO
```

Cela remplace directement les stratégies locales.

---

## 🔁 Importer des paramètres de sécurité uniquement
```
LGPO.exe /s C:\Chemin\GptTmpl.inf
```

---

## 🔧 Appliquer un fichier Registry `.pol`
### Import côté **Machine** :
```
LGPO.exe /m C:\Chemin\registry.pol
```

### Import côté **Utilisateur** :
```
LGPO.exe /u C:\Chemin\registry.pol
```

---

## 📝 Appliquer un fichier .REG directement dans les GPO locales
```
LGPO.exe /r C:\Chemin\parametres.reg
```

Cela convertit automatiquement le .REG en stratégie locale.

---

## 🧹 Réinitialiser complètement les GPO locales
```
LGPO.exe /r /p
```
> ⚠️ Attention : réinitialise toutes les stratégies locales (Machine + User).

---

## 👁️ Voir les commandes disponibles
```
LGPO.exe /?
```

---

## 📦 Exemple : automatisation d'un déploiement de GPO locale
```
LGPO.exe /b C:\BackupAvantModifs
LGPO.exe /g C:\MesParametresGPO
```

---

## ✔️ Recommandations
- Toujours faire une sauvegarde avant d'appliquer une GPO.
- Tester dans une VM avant utilisation en production.
- Éviter les .REG ambigus et préférer l'import de `.pol`.
- Utiliser LGPO dans des scripts PowerShell pour automatiser les postes.
