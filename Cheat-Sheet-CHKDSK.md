# Commandes CHKDSK et leurs options

| Commande            | Description |
|---------------------|-------------|
| `chkdsk`           | Vérifie le disque et affiche les erreurs sans les corriger. |
| `chkdsk /f`        | Corrige les erreurs détectées sur le disque. |
| `chkdsk /r`        | Localise les secteurs défectueux et tente de récupérer les données. Inclut `/f`. |
| `chkdsk /x`        | Force le démontage du volume avant la vérification. Inclut `/f`. |
| `chkdsk /scan`     | Analyse en ligne du disque (uniquement sur NTFS). |
| `chkdsk /spotfix`  | Répare uniquement les erreurs critiques (NTFS uniquement). |
| `chkdsk /perf`     | Améliore la vitesse d'analyse (nécessite `/scan`). |
| `chkdsk /b`        | Réévalue les secteurs défectueux sur un volume déjà marqué (inclut `/r`). |
| `chkdsk /v`        | Affiche les noms des fichiers lors de la vérification (NTFS) ou tous les fichiers du disque (FAT). |
| `chkdsk /f /r /x`  | Vérification complète + réparation + démontage forcé du volume. |

**Exemples d'utilisation :**
- Vérifier et réparer un disque :  
```
chkdsk C: /f /r /x
```
  
