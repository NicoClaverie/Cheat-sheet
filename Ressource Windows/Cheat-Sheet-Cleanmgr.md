### 🧹 cleanmgr (Nettoyage de disque Windows) Cheat Sheet

| Commande | Description |
| :--- | :--- |
| **`cleanmgr /d c`** | Lance l'utilitaire interactif pour le lecteur C:. |
| **`cleanmgr /sageset:1`** | Ouvre les réglages interactifs. **Sélectionne** les fichiers à nettoyer et enregistre la configuration sous l'ID **1**. |
| **`cleanmgr /sagerun:1`** | **Exécute** le nettoyage sans interaction, en utilisant les réglages enregistrés sous l'ID **1**. (Idéal pour l'automatisation/les scripts). |
| **`cleanmgr /lowdisk`** | Démarre l'outil avec la plupart des options cochées pour un nettoyage rapide en cas de manque d'espace. |
| **`cleanmgr /verylowdisk`** | Exécute un nettoyage automatique et agressif sans intervention de l'utilisateur. |

#### 🔑 Nettoyage Avancé (Fichiers Système)

Pour inclure des options comme le nettoyage des **Fichiers de mise à jour Windows (WinSxS)**, vous devez d'abord lancer l'outil avec des droits d'administrateur, soit en le lançant normalement puis en cliquant sur **"Nettoyer les fichiers système"**, soit en exécutant :

* **`cleanmgr /sageset:2`** (Exécuté en Admin) : Enregistrer une configuration incluant les fichiers système.
* **`cleanmgr /sagerun:2`** (Exécuté en Admin) : Lancer le nettoyage des fichiers système.
