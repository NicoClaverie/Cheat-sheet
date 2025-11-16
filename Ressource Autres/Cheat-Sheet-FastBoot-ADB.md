# Guide des commandes ADB et Fastboot (Tableau)

## 📱 ADB (Android Debug Bridge)

| Commande                              | Description                                         | Exemple d'utilisation                     |
| ------------------------------------- | --------------------------------------------------- | ------------------------------------------ |
| `adb devices`                         | Liste les appareils connectés                      | `adb devices`                              |
| `adb shell`                           | Ouvre un shell sur l'appareil                      | `adb shell`                                |
| `adb push <src> <dst>`                | Envoie un fichier vers l'appareil                  | `adb push file.txt /sdcard/`               |
| `adb pull <src> <dst>`                | Récupère un fichier depuis l'appareil              | `adb pull /sdcard/file.txt ./`             |
| `adb install <apk>`                   | Installe une application APK                       | `adb install app.apk`                      |
| `adb uninstall <package>`             | Désinstalle une application                        | `adb uninstall com.example.app`            |
| `adb reboot`                          | Redémarre l'appareil                               | `adb reboot`                               |
| `adb reboot bootloader`               | Redémarre en mode bootloader                       | `adb reboot bootloader`                    |
| `adb reboot recovery`                 | Redémarre en mode recovery                         | `adb reboot recovery`                      |
| `adb logcat`                          | Affiche les logs système                           | `adb logcat`                               |
| `adb sideload <zip>`                  | Installe une mise à jour ZIP via recovery          | `adb sideload update.zip`                  |
| `adb tcpip <port>`                    | Redémarre adb en mode TCP/IP sur le port spécifié  | `adb tcpip 5555`                           |
| `adb connect <ip>:<port>`             | Se connecte à un appareil via IP                   | `adb connect 192.168.1.100:5555`           |
| `adb disconnect`                      | Déconnecte les connexions réseau ADB               | `adb disconnect`                           |
| `adb shell pm list packages`          | Liste les paquets installés                        | `adb shell pm list packages`              |
| `adb shell settings get <namespace> <key>` | Récupère une valeur système via adb        | `adb shell settings get system screen_brightness` |
| `adb shell am start -n <package/activity>` | Lance une application via adb shell         | `adb shell am start -n com.android.settings/.Settings` |

---

## ⚙️ Fastboot (mode bootloader)

| Commande                              | Description                                         | Exemple d'utilisation                       |
| ------------------------------------- | --------------------------------------------------- | -------------------------------------------- |
| `fastboot devices`                    | Liste les appareils en mode fastboot                | `fastboot devices`                          |
| `fastboot getvar all`                 | Affiche toutes les variables système                | `fastboot getvar all`                       |
| `fastboot reboot`                     | Redémarre l'appareil                                | `fastboot reboot`                           |
| `fastboot flash recovery <img>`       | Flashe un recovery (ex: TWRP)                       | `fastboot flash recovery twrp.img`          |
| `fastboot boot <img>`                 | Boot temporaire sur une image                       | `fastboot boot twrp.img`                    |
| `fastboot flash boot <img>`           | Flashe l'image de boot                              | `fastboot flash boot boot.img`              |
| `fastboot format userdata`            | Formate les données (reset complet)                 | `fastboot format userdata`                  |
| `fastboot erase cache`                | Efface la partition cache                           | `fastboot erase cache`                      |
| `fastboot oem unlock`                 | Déverrouille le bootloader (ancienne méthode)       | `fastboot oem unlock`                       |
| `fastboot flashing unlock`            | Déverrouille le bootloader (Android >6.0)           | `fastboot flashing unlock`                  |
| `fastboot flash system <img>`         | Flashe la partition système                         | `fastboot flash system system.img`          |
| `fastboot flash vbmeta <img>`         | Flashe vbmeta pour les images signées               | `fastboot flash vbmeta vbmeta.img`          |
| `fastboot flashing lock`              | Re-verrouille le bootloader                         | `fastboot flashing lock`                    |
| `fastboot erase userdata`             | Efface les données utilisateur                      | `fastboot erase userdata`                   |
| `fastboot flashall`                   | Flashe toutes les partitions d’un firmware complet  | `fastboot flashall`                         |

---

> 📌 Remarques :
>
> - Sur certains appareils, le déverrouillage du bootloader nécessite une autorisation via un compte constructeur (ex: Xiaomi, Sony).
> - `adb` nécessite que le **débogage USB** soit activé dans les options développeur de l’appareil.
> - `fastboot` fonctionne uniquement si l'appareil est démarré en **mode bootloader**.


