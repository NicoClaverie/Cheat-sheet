
# Guide SSH - Secure Shell

## 🧾 Qu'est-ce que SSH ?

SSH (Secure Shell) est un protocole réseau chiffré permettant d’établir une connexion sécurisée entre deux ordinateurs.

---

## 📋 Tableau récapitulatif des commandes utiles

| Commande                              | Description                                              |
|--------------------------------------|----------------------------------------------------------|
| `ssh user@host`                      | Se connecter à une machine distante                     |
| `ssh -p 2222 user@host`              | Connexion via un port spécifique                        |
| `ssh-copy-id user@host`              | Copier sa clé publique sur le serveur distant           |
| `scp fichier user@host:/chemin/`    | Transférer un fichier vers le serveur                   |
| `scp user@host:/chemin/fichier ./`  | Télécharger un fichier depuis le serveur                |
| `ssh -L 8080:localhost:80 user@host` | Forward local : accès à un port distant localement      |
| `ssh -R 2222:localhost:22 user@host` | Reverse tunnel : exposer un port local sur un serveur   |
| `sftp user@host`                     | Connexion en mode SFTP pour gérer les fichiers          |
| `exit`                               | Fermer une session SSH                                  |

---

## 🔐 Clés SSH

```bash
ssh-keygen               # Générer une paire de clés
ssh-copy-id user@host   # Ajouter sa clé publique au serveur
```

---

## 🛠️ Autres commandes utiles

### 📁 Naviguer avec SFTP :
```bash
sftp user@host
```
Commandes disponibles en SFTP :
- `ls`, `cd`, `get`, `put`, `exit`, etc.

---

### 🔄 Reverse tunnel (accès à une machine derrière NAT) :
```bash
ssh -R 9000:localhost:22 user@serveur
```
Depuis le **serveur**, on peut ensuite se connecter avec :
```bash
ssh -p 9000 user@localhost
```

---

### 🔧 Configuration personnalisée (`~/.ssh/config`) :
```ini
Host monserveur
    HostName 192.168.1.100
    User toto
    Port 2222
    IdentityFile ~/.ssh/id_rsa
```
Connexion simplifiée :
```bash
ssh monserveur
```

---

## 🛡️ Astuces de sécurité

- Désactiver l'accès root :
  ```bash
  sudo nano /etc/ssh/sshd_config
  # Modifier : PermitRootLogin no
  ```
- Changer le port SSH :
  ```bash
  Port 2222
  ```
- Redémarrer le service :
  ```bash
  sudo systemctl restart ssh
  ```

---

## ⛔ Fermer la session

```bash
exit
```

---

## 📚 Ressources utiles

- [OpenSSH officiel](https://www.openssh.com/manual.html)
- `man ssh`, `man sshd`, `man ssh_config`, `man ssh-agent`
