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
