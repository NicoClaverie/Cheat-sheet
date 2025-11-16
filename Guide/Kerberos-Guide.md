# 🛡️ Kerberos - Guide Complet et Explication Détaillée

## 🧠 Introduction
Kerberos est un protocole d’authentification réseau sécurisé conçu pour permettre à deux entités (client et serveur) de prouver leur identité mutuelle sur un réseau non sécurisé.

Il repose sur un système de **tickets** et de **clés de chiffrement symétriques**, pour éviter de transmettre les mots de passe en clair.

Développé au MIT, Kerberos est aujourd’hui au cœur de nombreux environnements :
- Active Directory (Windows)
- UNIX / Linux (authentification via `sssd`, `krb5`)
- Services réseau (NFSv4, LDAP, SSH avec GSSAPI)

---

## ⚙️ Principe de fonctionnement
Kerberos s’appuie sur **trois entités principales** :

1. **Client** → utilisateur ou machine souhaitant accéder à une ressource.  
2. **KDC (Key Distribution Center)** → serveur central d’authentification.  
   - Contient deux sous-composants :
     - **AS (Authentication Server)**
     - **TGS (Ticket Granting Server)**
3. **Service cible** → serveur ou application que l’utilisateur souhaite atteindre (ex: serveur de fichiers).

---

## 🔐 Étapes du processus Kerberos

### 1️⃣ Authentification initiale (AS-REQ / AS-REP)
- Le client s’authentifie auprès du **KDC (AS)**.
- Il envoie son **identifiant** (pas le mot de passe).
- Le KDC vérifie l’identité et renvoie :
  - un **Ticket-Granting Ticket (TGT)** chiffré avec la clé du TGS ;
  - une **clé de session** chiffrée avec la clé dérivée du mot de passe de l’utilisateur.

💡 Le mot de passe n’est jamais envoyé sur le réseau.

---

### 2️⃣ Demande d’accès à un service (TGS-REQ / TGS-REP)
- Le client envoie le **TGT** au **TGS** et demande un ticket pour un service précis (ex: CIFS, LDAP…).
- Le TGS renvoie un **Service Ticket**, chiffré avec la clé du service.

---

### 3️⃣ Accès au service (AP-REQ / AP-REP)
- Le client envoie le **Service Ticket** au serveur.
- Le serveur le déchiffre (avec sa clé partagée avec le KDC).
- Si tout est valide, la connexion est établie (souvent via **SSO** — Single Sign-On).

---

## 🗝️ Détail des composants clés

| Élément | Description |
|----------|-------------|
| **KDC** | Serveur maître qui gère tous les secrets Kerberos. |
| **TGT** | Ticket maître permettant d’obtenir d’autres tickets sans ressaisir le mot de passe. |
| **Service Ticket** | Ticket spécifique à un service donné. |
| **Realm** | Domaine logique Kerberos (souvent en majuscules, ex: `AD.EXAMPLE.COM`). |
| **Principal** | Identité unique d’un utilisateur ou service (ex: `user@REALM` ou `cifs/server.example.com@REALM`). |
| **Keytab** | Fichier stockant les clés secrètes pour l’authentification automatique des services. |

---

## 🔎 Exemple concret : utilisateur sur domaine AD

1. Alice se connecte à Windows → son mot de passe est haché et comparé par le DC.  
2. Le DC (KDC) lui envoie un TGT.  
3. Lorsqu’elle accède à un partage réseau `\SERVEUR01\partage`, son poste demande un ticket au TGS.  
4. Le ticket est envoyé à `SERVEUR01`, qui l’accepte → connexion établie sans re-saisie du mot de passe.

---

## 🧩 Exemples Linux

### 📄 Fichier `/etc/krb5.conf`
```ini
[libdefaults]
  default_realm = EXAMPLE.COM
  dns_lookup_realm = true
  dns_lookup_kdc = true

[realms]
  EXAMPLE.COM = {
    kdc = kdc.example.com
    admin_server = kdc.example.com
  }

[domain_realm]
  .example.com = EXAMPLE.COM
  example.com = EXAMPLE.COM
```

### 🔧 Commandes utiles
```bash
kinit user@EXAMPLE.COM      # Obtenir un ticket (login)
klist                       # Voir les tickets actifs
kdestroy                    # Supprimer les tickets
kvno service/host@REALM     # Vérifier la validité d’un ticket de service
```

---

## 🧮 Schéma simplifié du flux Kerberos

```text
[Client] ── AS-REQ ──▶ [KDC:AS]
[Client] ◀─ AS-REP ── [KDC:AS]

[Client] ── TGS-REQ ─▶ [KDC:TGS]
[Client] ◀─ TGS-REP ── [KDC:TGS]

[Client] ── AP-REQ ──▶ [Service]
[Client] ◀─ AP-REP ── [Service] (optionnel)
```

---

## 🚧 Points de vigilance

| Problème | Cause fréquente | Solution |
|-----------|----------------|-----------|
| Erreur `KRB_AP_ERR_TKT_EXPIRED` | Ticket expiré | `kinit` pour renouveler le ticket |
| Horloge désynchronisée | Dérive de +5 min | Vérifier NTP (`timedatectl`) |
| “KDC unreachable” | DNS incorrect | Vérifier le `kdc` dans `krb5.conf` |
| Auth échoue via AD | Clé machine invalide | `kinit -k host/machine@REALM` ou ré-joindre le domaine |

---

## 🧰 Bonnes pratiques

- Toujours synchroniser les horloges via NTP.  
- Surveiller la durée de vie des tickets (`ticket_lifetime` et `renew_lifetime`).  
- Séparer les comptes de service (un par appli).  
- Restreindre les permissions des fichiers `keytab`.  
- Utiliser des DNS fiables et cohérents avec les Realms.  
- En environnement mixte (Linux/Windows), vérifier la compatibilité des types de chiffrement (`AES256`, `AES128`, `RC4`).

---

## 📚 Références
- RFC 4120 — *The Kerberos Network Authentication Service (V5)*  
- MIT Kerberos : https://web.mit.edu/kerberos/  
- Microsoft Docs : https://learn.microsoft.com/en-us/windows-server/security/kerberos/  
