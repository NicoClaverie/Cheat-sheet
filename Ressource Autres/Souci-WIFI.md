# Compatibilité Carte Réseau Récentes avec Bornes Wi-Fi Anciennes ( FICHIER TEMPORAIRE )

Ce document récapitule les points essentiels pour paramétrer une **carte réseau moderne** afin d'assurer la compatibilité et la stabilité avec des **bornes Wi-Fi anciennes**.

---

## 1. Incompatibilités fréquentes

| Situation                                                         | Symptômes typiques                                          |
| ----------------------------------------------------------------- | ----------------------------------------------------------- |
| Carte récente WiFi 6/6E → borne WiFi 4 (802.11n)                  | Connexion possible mais débits limités, parfois instable    |
| Carte avec canaux DFS/5 GHz avancés → borne 5 GHz ancienne        | Réseau absent ou disparaît de temps en temps                |
| Carte récente avec largeur de canal 80/160 MHz → borne max 40 MHz | Signal fluctuant, connexion instable                        |
| WPA3 activé sur carte → borne ancienne WPA2                       | Connexion impossible ou oscillations si mode mixte mal géré |
| Roaming / MU-MIMO / Beamforming moderne → borne ancienne          | Déconnexions, signal variable                               |

---

## 2. Solutions / Paramétrages côté carte réseau

1. **Forcer la carte sur un mode compatible avec la borne**

   * Exemples : 802.11n uniquement, ou mode mixte n/g
   * **Chemin Windows :** Gestionnaire de périphériques → Carte réseau → Propriétés → Avancé → Mode sans fil

2. **Limiter la largeur de canal**

   * 2.4 GHz : 20 MHz
   * 5 GHz : 40 MHz maximum
   * Évite les fluctuations liées à la négociation automatique

3. **Sécurité**

   * Désactiver WPA3 ou mode mixte si la borne est ancienne
   * Passer temporairement sur WPA2 seul

4. **Vérifier le firmware de la borne**

   * Même les bornes anciennes peuvent recevoir des correctifs pour la compatibilité

5. **Tester la stabilité**

   * Observer le RSSI (force du signal) et SNR (rapport signal/bruit) sur quelques minutes
   * Vérifier si les déconnexions ou variations disparaissent après les réglages

---

## 3. Conseils supplémentaires

* Si possible, **éviter les fonctionnalités avancées** comme MU-MIMO ou Beamforming si elles causent instabilité.
* Tester la carte sur une autre borne ou un autre réseau ancien pour confirmer que le problème vient de la compatibilité.
* Utiliser des outils comme **Acrylic WiFi** ou **WiFi Analyzer** pour visualiser la saturation des canaux et la stabilité du signal.

---

**Résumé rapide :**

* Forcer mode compatible
* Limiter largeur de canal
* Passer sur WPA2 si nécessaire
* Vérifier firmware borne
* Observer RSSI/SNR pour confirmer stabilité


## Analyse du wifi

Acrylic Wi-Fi Analyser  
https://www.acrylicwifi.com/wifi-analyzer/
