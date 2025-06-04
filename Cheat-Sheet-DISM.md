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

## 🛑 Astuces

- `Online` = système en cours d’exécution
- `Image:D:\` = système hors-ligne (ex: depuis WinRE)
- Toujours vérifier l’espace disque libre
- Pour éviter les erreurs, désactiver l’antivirus le temps de la commande

---
