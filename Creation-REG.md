# Aide-Mémoire Fichier de Registre Windows (.reg)

## 1. Structure de Base

Tous les fichiers .reg doivent commencer par l'en-tête de version.

```
Windows Registry Editor Version 5.00
```

## 2. Créer / Modifier une Valeur
Utilisé pour ajouter une nouvelle clé ou modifier une valeur existante.

```
Windows Registry Editor Version 5.00

[Chemin\Complet\De\La\Clé]
"NomDeLaValeur"=type:donnée
```

## 3. Exemples de Types de Données

|Type|Format dans le .reg|Explication|
|:-:|:-:|:-:|
|REG_SZ|`"Texte en clair"`|Chaîne de caractères standard.|
|REG_DWORD|`dword:00000001`|Nombre 32 bits (souvent 0 ou 1 pour Activer/Désactiver).|
|REG_QWORD|`qword:0000000000000001`|Nombre 64 bits.|
|REG_BINARY|`hex:01,00,00,00`|Données binaires.|

## 4. Supprimer des Éléments

**A. Supprimer une Clé (Dossier)**  
Ajouter un tiret (`-`) devant le chemin complet de la clé. **Attention** : supprime la clé et tout son contenu.

```
Windows Registry Editor Version 5.00

[-Chemin\Complet\De\La\Clé\ASupprimer]
```

**B. Supprimer une Valeur (Élément spécifique)**  
Ajouter un tiret (`-`) comme donnée de la valeur.

```
Windows Registry Editor Version 5.00

[Chemin\Complet\De\La\Clé]
"NomDeLaValeurASupprimer"=-
```

## 5. Exemple Demandé (Création d'un DWORD 1)  
Créer une valeur `MaNouvelleValeur` de type DWORD avec la donnée 1 dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System.`

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System]
"MaNouvelleValeur"=dword:00000001
```

**Note** : L'importation de fichiers .reg sous `HKEY_LOCAL_MACHINE` nécessite des droits d'administrateur.
