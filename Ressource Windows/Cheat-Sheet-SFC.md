
# 🛠️ Cheat Sheet : SFC (System File Checker)

## 🔍 Que fait `sfc` ?
`sfc` (System File Checker) permet d'analyser et de réparer les fichiers système corrompus de Windows.

---

## 📌 Commandes de base

### ✅ Analyse sans correction :
```
sfc /verifyonly
```
> Analyse les fichiers système sans tenter de les réparer.

### 🔧 Analyse + réparation automatique :
```
sfc /scannow
```
> Analyse l'intégrité des fichiers système et les répare si possible.

---

## 💾 Mode hors ligne (WinRE / autre OS) :
Si Windows ne démarre pas, on peut scanner une installation offline.

### Exemple :
```
sfc /scannow /offbootdir=D:\ /offwindir=D:\Windows
```
> - `D:` = lettre de la partition système dans l'environnement WinRE.
> - `D:\Windows` = dossier contenant Windows à réparer.

---

## ⚠️ Erreurs courantes

### "La protection des ressources Windows n'a pas réussi à démarrer le service de réparation" :
- Peut indiquer une base de registre ou des fichiers système endommagés.
- Lancer `dism` avant `sfc` peut corriger cela.

### "Impossible de démarrer le service de réparation" :
- Peut être causé par l'absence ou l'échec du service `TrustedInstaller`.
- En WinRE, ce service peut ne pas fonctionner correctement.

---

## 📁 Fichiers de log
Les résultats sont enregistrés dans :
```
C:\Windows\Logs\CBS\CBS.log
```
À consulter pour voir quels fichiers ont été réparés ou non.

---

## 🔄 Ordre recommandé de réparation (offline)
1. D’abord réparer l’image avec DISM :
```
dism /Image:D:\ /Cleanup-Image /RestoreHealth /Source:E:\sources\install.wim /LimitAccess
```
2. Ensuite lancer SFC offline :
```
sfc /scannow /offbootdir=D:\ /offwindir=D:\Windows
```

---

## 🧼 Nettoyage des logs CBS (facultatif)
```
del /f /q C:\Windows\Logs\CBS\*.log
```

---

## 📚 Astuce bonus
Pense à monter ta ruche registre pour diagnostiquer si besoin :
```
reg load HKLM\OfflineSOFTWARE D:\Windows\System32\config\SOFTWARE
reg query HKLM\OfflineSOFTWARE\Microsoft\Windows NT\CurrentVersion
reg unload HKLM\OfflineSOFTWARE
```
