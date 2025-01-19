
# Cheat Sheet : Commande `net user` sous Windows

## ⚡ Introduction
`net user` est une commande Windows qui permet de gérer les utilisateurs locaux. Elle peut être utilisée pour créer, modifier ou supprimer des comptes utilisateurs, et pour configurer leurs paramètres.

---

## 🛠️ Commandes générales
| Commande                | Description                                   |
|-------------------------|-----------------------------------------------|
| `net user`              | Liste tous les comptes utilisateurs locaux.  |
| `net user <NomUtilisateur>` | Affiche les détails d’un utilisateur spécifique. |

---

## 🌟 Création et modification de comptes
| Commande                                      | Description                                                     |
|-----------------------------------------------|-----------------------------------------------------------------|
| `net user <NomUtilisateur> <MotDePasse> /add` | Crée un nouvel utilisateur avec un mot de passe.               |
| `net user <NomUtilisateur> * /add`           | Crée un nouvel utilisateur et demande un mot de passe.          |
| `net user <NomUtilisateur> <MotDePasse>`     | Change le mot de passe d’un utilisateur existant.               |
| `net user <NomUtilisateur> /fullname:"Nom Complet"` | Change le nom complet affiché pour l’utilisateur.            |
| `net user <NomUtilisateur> /active:yes`      | Active un compte utilisateur désactivé.                        |
| `net user <NomUtilisateur> /active:no`       | Désactive un compte utilisateur.                               |

---

## 🔒 Gestion des mots de passe
| Commande                                    | Description                                                    |
|---------------------------------------------|----------------------------------------------------------------|
| `net user <NomUtilisateur> *`               | Demande de changer le mot de passe d’un utilisateur.           |
| `net user <NomUtilisateur> /passwordchg:yes`| Autorise l’utilisateur à changer son mot de passe.             |
| `net user <NomUtilisateur> /passwordchg:no` | Interdit à l’utilisateur de changer son mot de passe.          |
| `net user <NomUtilisateur> /logonpasswordchg:yes` | Force l’utilisateur à changer son mot de passe au prochain logon. |

---

## 🔐 Paramètres avancés
| Commande                                       | Description                                                    |
|------------------------------------------------|----------------------------------------------------------------|
| `net user <NomUtilisateur> /expires:JJ/MM/AAAA`| Définit une date d’expiration pour le compte.                  |
| `net user <NomUtilisateur> /homedir:"<Chemin>"`| Définit un dossier personnel pour l’utilisateur.               |
| `net user <NomUtilisateur> /times:M-F,08:00-17:00` | Définit les heures de connexion autorisées.                    |
| `net user <NomUtilisateur> /comment:"<Commentaire>"` | Ajoute un commentaire au compte utilisateur.                 |

---

## ❌ Suppression de comptes
| Commande                     | Description                     |
|------------------------------|---------------------------------|
| `net user <NomUtilisateur> /delete` | Supprime un utilisateur.       |

---

## 🎯 Exemple pratique
### Créer un compte utilisateur :
```cmd
net user JohnDoe MySecurePass123 /add
```
### Désactiver un utilisateur :
```cmd
net user JohnDoe /active:no
```
### Forcer un changement de mot de passe au prochain logon :
```cmd
net user JohnDoe /logonpasswordchg:yes
```

---

## 📘 Notes
- **Droits administratifs** : Certaines commandes nécessitent des privilèges élevés.
- **Comptes locaux uniquement** : La commande `net user` ne fonctionne pas pour les comptes Active Directory.

---
