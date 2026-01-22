# Aide mémoire Sysprep


## 🛠️ Les commandes de base  
La syntaxe générale est la suivante :  
`sysprep.exe [/oobe | /audit] [/generalize] [/reboot | /shutdown | /quit] [/unattend:fichier.xml]`  

**Les modes principaux**  

- `/oobe` (Out-of-Box Experience) : Redémarre l'ordinateur en mode "bienvenue". C'est ce que voit l'utilisateur final (choix de la langue, création de compte, etc.).
- `/audit` : Redémarre l'ordinateur en mode Audit. Cela permet d'installer des pilotes ou des applications supplémentaires avant la capture de l'image, sans créer de compte utilisateur.

**Les options cruciales** : 

- `/generalize` Indispensable pour le clonage. Supprime les informations uniques (SID), réinitialise l'activation Windows (Rearm) et nettoie les journaux d'événements.
- `/unattend:nom_du_fichier.xml` : Applique les paramètres d'un fichier de réponse pour automatiser l'installation.

---

## 🚀 Scénarios courants

**1. Préparer une image pour le clonage (Le plus fréquent)**

C'est la commande standard pour "sceller" un PC avant de capturer son image avec Ghost, Clonezilla ou MDT.

```
Bashsysprep /generalize /oobe /shutdown
```
**2. Passer en mode Audit pour personnaliser l'image**

Si tu viens d'installer Windows et que tu veux installer des logiciels sans créer de profil utilisateur définitif.
```
Bashsysprep /audit /reboot
```
**3. Automatiser avec un fichier de réponse**

Pour éviter de répondre manuellement aux questions lors du premier démarrage.
```
Bashsysprep /generalize /oobe /shutdown /unattend:C:\temp\autounattend.xml
```

---

## 📋 Tableau récapitulatif des drapeaux (Flags)

|Flag|Description|
|:-:|:-:|
|`/generalize`|Supprime le SID et les infos spécifiques au matériel.|
|`/oobe`|Lance l'assistant de configuration au prochain démarrage.|
|`/audit`|Permet de modifier l'image avant le déploiement final.|
|`/shutdown`|Éteint le PC une fois l'opération terminée (prêt pour la capture).|
|`/reboot`|Redémarre immédiatement.|
|`/quit`|Ferme Sysprep sans éteindre ni redémarrer après l'exécution.|

## ⚠️ Conseils et pièges à éviter

- **Emplacement :** L'exécutable se trouve toujours dans `%WINDIR%\system32\sysprep\`.
- **Limite de "Rearm" :** Tu ne peux pas utiliser `/generalize` plus de 8 fois sur une même image Windows (limite de réinitialisation de la licence).
- **Applications Windows Store (AppX) :** C'est la cause n°1 d'échec de Sysprep. Si tu as mis à jour des apps Windows Store, Sysprep peut bloquer. Il faut souvent supprimer les paquets incriminés via PowerShell.
- **Mode VM :** Si tu es sur une machine virtuelle, utilise l'option /mode:vm (disponible sur les versions récentes) pour accélérer le processus si tu ne changes pas de matériel virtuel.
