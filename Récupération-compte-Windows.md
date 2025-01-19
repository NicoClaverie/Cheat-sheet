
# Réinitialiser un mot de passe Windows en remplaçant `utilman.exe` ou `sethc.exe`

## ⚠️ Avertissements
- Cette méthode est réservée à des fins légitimes (par exemple, récupérer l'accès à un compte dont vous êtes propriétaire).
- Elle nécessite un support de réparation Windows (clé USB ou DVD).
- Une utilisation non autorisée est illégale.

---

## Étapes détaillées

### 1. Démarrer à partir d’un support de réparation Windows
1. Insérez une clé USB ou un DVD d'installation Windows.
2. Configurez le BIOS/UEFI pour démarrer sur ce support.
3. Une fois l’écran d’installation affiché, cliquez sur **Réparer l’ordinateur** (en bas à gauche).

---

### 2. Ouvrir une invite de commandes
1. Allez dans **Dépannage** → **Options avancées** → **Invite de commandes**.
2. Identifiez la lettre du disque où Windows est installé (généralement `C:`). Utilisez la commande suivante pour vérifier :
   ```
   dir C:\
   ```

---

### 3. Remplacer `utilman.exe` ou `sethc.exe` par `cmd.exe`
1. Naviguez vers le dossier `System32` :
   ```
   cd C:\Windows\System32
   ```
2. Renommez `utilman.exe` en `utilman.bak` ou `sethc.exe` en `sethc.bak` pour en conserver une copie :
   ```
   copy utilman.exe utilman.bak
   ```
     
   ```
   copy sethc.exe sethc.bak
   ```

3. Remplacez `utilman.exe` ou `sethc.exe` par `cmd.exe` :
   ```
   copy cmd.exe utilman.exe
   ```
  
   ```
   copy cmd.exe sethc.exe
   ```
---

### 4. Redémarrer l’ordinateur
- Fermez toutes les fenêtres et redémarrez normalement.

---

### 5. Utiliser l’invite de commandes pour réinitialiser le mot de passe
1. Si vous avez choisi de remplacer `utilman.exe`, sur l’écran de connexion, cliquez sur l’icône **Accessibilité** (en bas à droite).  
  Une invite de commande s’ouvrira (au lieu des options d’ergonomie).  
  
2. Si vous avez choisi de remplacer `sethc.exe` appuyez rapidement 5 fois de suite sur la touche majuscule. En temps normal, cela lance l’utilitaire des touches rémanentes mais dans notre cas, cela aura pour effet d’ouvrir une invite de commande.

2. Réinitialisez le mot de passe de l’utilisateur souhaité :
   ```
   net user <NomUtilisateur> <NouveauMotDePasse>
   ```
   Exemple :
   ```
   net user Administrateur Password123
   ```

---

### 6. Restaurer `utilman.exe` ou `sethc.exe`
1. Une fois connecté, ouvrez une invite de commande avec des droits administratifs.
2. Replacez le fichier original :
   ```
   copy C:\Windows\System32\utilman.bak C:\Windows\System32\utilman.exe
   ```
     
   ```
   copy C:\Windows\System32\sethc.bak C:\Windows\System32\sethc.exe
   ```

---

## Points importants
- **BitLocker** : Si le disque est protégé par BitLocker, la clé de récupération sera nécessaire.
- **Compte Microsoft** : Si vous utilisez un compte Microsoft, il est souvent plus simple de réinitialiser le mot de passe en ligne.

---

## Exemple de commande pour réinitialiser un mot de passe
   ```
   net user Utilisateur Test123
   ```
Cela définit le mot de passe de l'utilisateur `Utilisateur` à `Test123`.

---

### ⚠️ Avertissement final
Cette méthode doit être utilisée uniquement dans des situations autorisées. L’usage abusif peut entraîner des sanctions légales.
