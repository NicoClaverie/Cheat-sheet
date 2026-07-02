# Cheat-Sheet-PS-FireWall

Voici un **cheat sheet (aide-mémoire) pour la gestion du pare-feu Windows via PowerShell**, basé sur le module `NetSecurity` introduit depuis Windows Server 2012.

### 🛠️ Prérequis et Informations Générales
*   **Module concerné :** `NetSecurity`.
*   **Lister toutes les commandes du pare-feu :** 
    `Get-Command -Module NetSecurity`
*   **Les profils du pare-feu :** Les commandes s'appliquent sur des profils spécifiques. Les valeurs possibles sont **Domain** (Réseaux avec domaine), **Private** (Réseaux privés), **Public** (Réseaux publics ou invités) ou **\*** (Tous les profils).

---

### 🛡️ 1. Vérifier et Gérer l'État du Pare-feu
*   **Vérifier si le pare-feu est actif sur les profils :**
    `Get-NetFirewallProfile | ft Name,Enabled`
*   **Activer le pare-feu sur tous les profils :**
    `Set-NetFirewallProfile -Profile * -Enabled True`
*   **Désactiver le pare-feu sur des profils spécifiques** (ex: tous) :
    `Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False`
*   **Activer le pare-feu sur un seul profil** (ex: Public) :
    `Set-NetFirewallProfile -Profile Public -Enabled true`

---

### 📋 2. Utiliser les Groupes de Règles Prédéfinies
Windows intègre des groupes de règles pour simplifier l'autorisation de services courants (comme le Bureau à distance) sans avoir à chercher les ports manuellement.
*   **Lister les groupes de règles disponibles :**
    ```powershell
    $rules=Get-NetFirewallRule   
    $DisplayGroups=foreach ($rule in $rules){$rule.displaygroup}   
    $DisplayGroups | Select-Object -Unique
    ```
*   **Créer une règle à partir d'un groupe prédéfini** (ex: Bureau à distance) :
    `New-NetFirewallRule -DisplayName "Autoriser le Bureau à distance (RDP)" -Group "Bureau à distance" -Profile Domain -Enabled True -Action Allow`

---

### ➕ 3. Créer une Règle Personnalisée
Pour des besoins spécifiques, vous pouvez créer vos propres règles de flux entrants ou sortants.
*   **Exemple de création de règle (Autoriser SSH sur le port 22 en TCP) :**
    `New-NetFirewallRule -Name "SSH" -DisplayName "Autoriser SSH (Port 22)" -Profile Domain -Enabled True -Protocol TCP -LocalPort 22 -Action Allow -LocalAddress 192.168.100.13`

**Les paramètres principaux à retenir :**
*   **Name / DisplayName :** Nom unique de la règle / Nom d'affichage.
*   **Profile :** Profil cible (Domain, Private, Public).
*   **Enabled :** Active (`True`) ou désactive (`False`) la règle.
*   **Protocol / LocalPort :** Le protocole (`TCP`/`UDP`) et le port local visé.
*   **Action :** Autoriser (`Allow`) ou bloquer (`Block`).
*   **LocalAddress / RemoteAddress :** L'adresse IP locale de la machine ou l'adresse IP distante concernée.
*   **Direction :** Indique si la règle s'applique au trafic entrant (`Inbound`) ou sortant (`Outbound`).
*   **Program / Service :** Permet d'appliquer la règle à une application ou un service spécifique.

---

### ✏️ 4. Modifier ou Désactiver une Règle Existante
Plutôt que de supprimer une règle, il est possible de la désactiver temporairement pour la conserver.
*   **Désactiver une règle existante (ex: "SSH") :**
    `Set-NetFirewallRule -Name SSH -Enabled false`
*   **Vérifier le statut d'une règle précise :**
    `(Get-NetFirewallRule -Name SSH).Enabled` *(Retournera `False` si elle est désactivée)*.

---

### ❌ 5. Supprimer une Règle
Si une règle n'est plus du tout utilisée, vous pouvez la supprimer définitivement de la configuration.
*   **Supprimer une règle (ex: "SSH") :**
    `Remove-NetFirewallRule -Name SSH`
*   **Vérifier la suppression :** 
    `Get-NetFirewallRule -Name SSH` *(Si la suppression a fonctionné, PowerShell retournera un message d'erreur)*.

---

Voici un tableau récapitulatif des commandes PowerShell du module `NetSecurity` pour gérer le pare-feu Windows :

| Action souhaitée | Commande PowerShell | Description / Paramètres |
| :--- | :--- | :--- |
| **Lister les commandes du pare-feu** | `Get-Command -Module NetSecurity` | Affiche toutes les commandes (cmdlets) disponibles dans le module NetSecurity. |
| **Vérifier l'état du pare-feu** | `Get-NetFirewallProfile \| ft Name,Enabled` | Affiche si le pare-feu est actif ou inactif sur les différents profils (Domain, Private, Public). |
| **Activer le pare-feu globalement** | `Set-NetFirewallProfile -Profile * -Enabled True` | Active le pare-feu sur tous les profils (utiliser `*` cible tous les profils en une fois). |
| **Désactiver le pare-feu spécifiquement** | `Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False` | Désactive le pare-feu sur les profils spécifiés (déconseillé en production). |
| **Lister les groupes prédéfinis** | `$rules=Get-NetFirewallRule`<br>`$DisplayGroups=foreach...` | Permet d'afficher la liste unique des groupes de règles préconfigurés par Windows. |
| **Créer une règle depuis un groupe** | `New-NetFirewallRule -Group "Bureau à distance" ...` | Crée une règle basée sur un groupe existant (via le paramètre `-Group`) pour simplifier l'autorisation des services. |
| **Créer une règle personnalisée** | `New-NetFirewallRule -Name "SSH" -Protocol TCP -LocalPort 22 -Action Allow ...` | Crée une nouvelle règle. Nécessite de préciser le nom, le profil, le protocole (`TCP`/`UDP`), le port cible, et l'action (`Allow`/`Block`). |
| **Désactiver une règle spécifique** | `Set-NetFirewallRule -Name SSH -Enabled false` | Modifie une règle existante pour la désactiver sans la supprimer. |
| **Vérifier le statut d'une règle** | `(Get-NetFirewallRule -Name SSH).Enabled` | Retourne la valeur `True` ou `False` selon si la règle est activée ou non. |
| **Supprimer une règle** | `Remove-NetFirewallRule -Name SSH` | Supprime définitivement la règle correspondante de la configuration du pare-feu. |

**Paramètres clés à retenir lors de la création (`New-NetFirewallRule`) :**
*   **-Profile** : `Domain`, `Private`, `Public` ou `*`.
*   **-Direction** : Trafic entrant (`inbound`) ou sortant (`outbound`).
*   **-LocalAddress / -RemoteAddress** : Cible une adresse IP locale ou distante spécifique.
*   **-Program / -Service** : Applique la règle uniquement à une application ou un service précis.


Source : https://www.it-connect.fr/chapitres/gerer-le-pare-feu-en-powershell/
