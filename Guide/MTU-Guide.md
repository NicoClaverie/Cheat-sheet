# 🧠 Cheat Sheet — MTU, MSS et Fragmentation Réseau

---

## ⚙️ Définitions rapides

| Terme | Signification | Niveau OSI | Remarque |
|-------|----------------|-------------|-----------|
| **MTU** | Maximum Transmission Unit | Couche 2 (liaison) | Taille max d’un paquet IP qu’une interface peut transporter sans fragmentation. |
| **MSS** | Maximum Segment Size | Couche 4 (TCP) | Taille max de données TCP (hors en-têtes IP/TCP). |
| **PMTUD** | Path MTU Discovery | Couche 3 | Mécanisme pour découvrir la plus petite MTU sur le chemin. |

---

## 📏 Valeurs typiques

| Type de lien | MTU (octets) | MSS IPv4 (MTU - 40) | MSS IPv6 (MTU - 60) |
|---------------|---------------|-----------------------|-----------------------|
| Ethernet standard | 1500 | 1460 | 1440 |
| PPPoE | 1492 | 1452 | 1432 |
| VPN (IPsec) | 1400–1450 | 1360–1410 | 1340–1390 |
| VLAN (802.1Q) | 1496 | 1456 | 1436 |
| Jumbo Frame | 9000 | 8960 | 8940 |

---

## 🔍 Formules essentielles

```text
MSS = MTU - Header_IP - Header_TCP
IPv4 : MSS = MTU - 20 - 20
IPv6 : MSS = MTU - 40 - 20
```

**Exemple :**
```text
MTU 1500 → MSS IPv4 = 1500 - 40 = 1460
```

---

## 🧩 Fragmentation IPv4 (rappel)

- Si un paquet > MTU, il est fragmenté sauf si DF = 1 (Don't Fragment).  
- Chaque fragment a :
  - son propre header IP
  - champ **Offset** (multiples de 8 octets)
  - flag **MF** (More Fragments)

**IPv6** : aucun routeur ne fragmente → seul l’émetteur peut le faire.  
Si le paquet est trop gros → message **ICMPv6 Packet Too Big**.

---

## 🚧 Path MTU Discovery (PMTUD)

| Protocole | Mécanisme | Message ICMP |
|------------|------------|----------------|
| IPv4 | DF=1 + ICMP "Fragmentation needed" | Type 3 Code 4 |
| IPv6 | ICMPv6 "Packet Too Big" | Type 2 |

**⚠️ Si ICMP bloqué → PMTUD échoue → “black hole” TCP (connexion figée).**

**Solutions :**
- Autoriser ICMP nécessaires.
- Ou appliquer **MSS Clamping** sur le routeur/NAT.

---

## 🧰 Commandes pratiques

### 🔹 Linux
```bash
# Afficher MTU
ip link show dev eth0

# Changer MTU
sudo ip link set dev eth0 mtu 1400

# Tester la MTU avec ping (IPv4)
ping -M do -s 1472 8.8.8.8
# 1472 + 28 (en-têtes IP+ICMP) = 1500
# Réduire jusqu’à trouver la plus grande taille qui passe.

# Découvrir la MTU du chemin
tracepath 8.8.8.8
```

### 🔹 Windows
```powershell
# Tester MTU
ping -f -l 1472 8.8.8.8

# Changer MTU d'une interface
netsh interface ipv4 set subinterface "Ethernet" mtu=1400 store=persistent
```

---

## 🔧 MSS Clamping (Linux)
Permet d’éviter les problèmes PMTUD si ICMP bloqué :
```bash
iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN \
  -j TCPMSS --clamp-mss-to-pmtu
```
➡️ Ajuste automatiquement le MSS à la plus petite MTU détectée.

---

## 🧪 Calcul rapide à retenir

| Situation | MTU | MSS IPv4 |
|------------|------|-----------|
| Ethernet standard | 1500 | 1460 |
| PPPoE | 1492 | 1452 |
| VPN IPSec | 1400 | 1360 |
| VLAN 802.1Q | 1496 | 1456 |

---

## 🛠 Dépannage express

| Symptôme | Cause probable | Solution |
|-----------|----------------|-----------|
| Sites lents / qui ne chargent pas | PMTUD bloqué (ICMP filtré) | Autoriser ICMP ou MSS clamp |
| VPN qui “freeze” | MTU trop haute | Baisser MTU à 1400/1380 |
| Ping OK mais gros transferts KO | Fragmentation bloquée | Tester avec `ping -M do` |
| Différents MTU sur le LAN | Incohérence d’interface | Harmoniser les MTU |

---

## 🧮 Exemple concret
MTU physique : 1500  
Tunnel VPN ajoute 60 octets overhead  
→ MTU utile = 1440  
→ MSS IPv4 = 1440 − 40 = **1400**

---

## 💡 Rappels rapides

✅ **MTU = taille max paquet IP par interface**  
✅ **MSS = MTU - 40 (IPv4) ou -60 (IPv6)**  
✅ **IPv4 fragmente, IPv6 ne fragmente pas (Packet Too Big)**  
✅ **Toujours tester avec `ping -M do` ou `tracepath`**  
✅ **MSS Clamping = sécurité anti-bug PMTUD**  
✅ **Jumbo Frames = gain local, pas sur Internet**

---

# 🧠 Cheat Sheet — Paramètres Réseau et MTU avancés

---

## 🔸 1. MSS (Maximum Segment Size)
- Dépend du MTU, peut être forcé côté client, routeur ou pare-feu.
- Évite fragmentation ou blocage sur VPN/tunnels.

**Linux / Routeur : MSS Clamping**
```bash
iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN \
  -j TCPMSS --clamp-mss-to-pmtu
```

---

## 🔸 2. TCP MTU Probing (Linux)
```bash
# Voir état
sysctl net.ipv4.tcp_mtu_probing

# Valeurs
# 0 = désactivé, 1 = actif si PMTUD échoue, 2 = toujours actif
sudo sysctl -w net.ipv4.tcp_mtu_probing=1
```

---

## 🔸 3. IPv6 MTU minimum
- IPv6 impose MTU ≥ 1280 octets.
```bash
ip -6 link show dev eth0
```

---

## 🔸 4. Jumbo Frames
- Permet gain débit sur LAN.
```bash
ip link show dev eth0
sudo ip link set dev eth0 mtu 9000
```
⚠️ Tous les équipements doivent supporter le même MTU.

---

## 🔸 5. Offloading (TSO, LRO, GRO, GSO)
- Vérifier :
```bash
ethtool -k eth0 | grep offload
```
- Désactiver si anomalies :
```bash
sudo ethtool -K eth0 tso off gso off gro off
```

---

## 🔸 6. ICMP / ICMPv6 Filtering
- Essentiel pour PMTUD
```bash
iptables -A INPUT -p icmp -j ACCEPT
ip6tables -A INPUT -p icmpv6 -j ACCEPT
```

---

## 🔸 7. MTU dans tunnels / interfaces virtuelles
- VPN, Docker, bridges KVM : vérifier MTU
```bash
ip link set wg0 mtu 1420  # exemple WireGuard
```

---

## 🔸 8. Path MTU Discovery et conteneurs / VM
- Assurer que ICMP traverse bridges et interfaces virtuelles.
- Sinon appliquer MSS clamp sur passerelle virtuelle.

---

## 🔸 9. sysctl réseau liés à fragmentation et PMTUD
```bash
sysctl net.ipv4.ip_no_pmtu_disc=0
sysctl net.ipv4.ipfrag_low_thresh
sysctl net.ipv4.ipfrag_high_thresh
sysctl net.ipv4.route.min_pmtu
```

---

## 🔸 10. Surveillance et diagnostic
- `tracepath <host>` → MTU du chemin
- `tcpdump -i eth0 icmp` → messages "fragmentation needed"
- `wireshark` → filtre `icmp or icmpv6`
- `ip route get <host>` → MTU connue sur la route
- `ss -i` → MSS négociée pour session TCP

---

## ✅ Récapitulatif des commandes clés
| Catégorie | Commande | Objectif |
|-----------|----------|----------|
| MTU | `ip link show dev eth0` | Taille max par interface |
| MSS | `iptables --clamp-mss-to-pmtu` | Ajuster MSS automatiquement |
| PMTUD | `sysctl net.ipv4.tcp_mtu_probing=1` | Découverte dynamique MTU |
| ICMP | `iptables -A INPUT -p icmp -j ACCEPT` | Laisser passer découverte MTU |
| Offloading | `ethtool -k eth0` | Vérifier TSO/GSO/GRO |
| VPN MTU | `ip link set wg0 mtu 1420` | Adapter au protocole |
| Diagnostic | `tracepath`, `ping -M do`, `tcpdump icmp` | Tester et observer MTU |
