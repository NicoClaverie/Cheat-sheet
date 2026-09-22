# Mode opératoire : Remplacement du dossier Default sous WinRE

## Prérequis
- Avoir démarré le PC sur l'environnement de récupération **WinRE** (Invite de commandes).
- Identifier la lettre de la partition système Windows (par défaut `C:` dans la suite de ce guide).

---

## Étape 1 : Sauvegarder le dossier Default d'origine

1. Prendre la propriété du dossier `Default` :
    ```cmd
    takeown /f C:\Users\Default /a /r /d o
    ```
2. Accorder les droits complets au groupe Administrateurs :

    ```cmd
    icacls C:\Users\Default /grant Administrateurs:F /t
    ```

3. Retirer les attributs de masquage et système :

    ```cmd
    attrib -h -s -r C:\Users\Default
    ```

4. Renommer le dossier actuel pour créer une sauvegarde :

    ```cmd
    ren C:\Users\Default Default.old
    ```

## Étape 2 : Mettre en place le nouveau dossier Default

1. Renommer le dossier modèle (ex: NouveauDossier) en Default :

    ```cmd
    ren C:\Users\NouveauDossier Default
    ```

2. Appliquer les attributs système et caché requis par Windows :

    ```cmd
    attrib +h +s C:\Users\Default
    ```

## Étape 3 : Nettoyer le compte temporaire/modèle (Optionnel)

1. Supprimer l'utilisateur temporaire utilisé pour créer le modèle :

    ```cmd
    net user NomDuCompteTemp /delete
    ```

2. Supprimer son dossier resté dans `C:\Users` :

    ```cmd
    rmdir /s /q C:\Users\NomDuCompteTemp
    ```

3. Ouvrir l'outil d'exécution avec le raccourci `Win + R`.

4. Taper la commande suivante et valider :

    ```cmd
    regedit
    ```

5. Naviguer vers le dossier suivant :  

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList`

6. Parcourir les clés nommées `S-1-5-21-...` dans le panneau de gauche.

7. Sélectionner chaque clé et vérifier la donnée ProfileImagePath dans le panneau de droite.

8. Repérer la clé dont la valeur correspond à `C:\Users\NomDuCompteTemp`.

9. Faire un clic droit sur cette clé `S-1-5-21-...` et cliquer sur Supprimer.

10. Fermer l'Éditeur du Registre.

## Étape 4 : Vérification du succès

1. Lister le contenu de `C:\Users` pour valider la structure :

    ```cmd
    dir /a C:\Users
    ```
    Vérifiez la présence du dossier `Default` et de la jonction `Default User [C:\Users\Default]`.


## Étape complémentaire : Appliquer les permissions (NTFS/ACL) sur le dossier Default

Dans l'invite de commandes (en administrateur sous Windows ou depuis WinRE) :

1. Réinitialiser et appliquer l'héritage des autorisations :

    ```cmd
    icacls C:\Users\Default /reset /t /c /l /q
    ```

2. Accorder le contrôle total aux Administrateurs et au Système :

    ```cmd
    icacls C:\Users\Default /grant Administrateurs:(OI)(CI)F /T
    icacls C:\Users\Default /grant SYSTEM:(OI)(CI)F /T
    ```
3. Accorder les droits de lecture et exécution au groupe Utilisateurs (nécessaire pour copier le profil lors de la création d'un compte) :

    ```cmd
    icacls C:\Users\Default /grant Utilisateurs:(OI)(CI)RX /T
    ```

    (Remarque : sur un système en anglais, remplacez `Administrateurs` par `Administrators` et `Utilisateurs` par `Users`).

## Étape complémentaire 2 : Supprimer les droits de l'ancien utilisateur sur le dossier Default

Dans l'invite de commandes (en Administrateur sous Windows ou depuis WinRE) :

1. Supprimer les permissions explicites attribuées à l'ancien utilisateur (remplacez `NomAncienUtilisateur` par le compte d'origine, ex: `TEMP`) :

    ```cmd
    icacls C:\Users\Default /remove NomAncienUtilisateur /t /c /l /q
    ```

2. Réinitialiser les autorisations pour rétablir la transmission propre des héritages NTFS :

    ```cmd
    icacls C:\Users\Default /reset /t /c /l /q
    ```

3. Rétablir le groupe SYSTEM en tant que propriétaire d'origine du dossier :

    ```cmd
    icacls C:\Users\Default /setowner "NT AUTHORITY\SYSTEM" /t /c /l /q
    ```

    *(Remarque : sous WinRE, si la commande précédente échoue, vous pouvez utiliser icacls `C:\Users\Default /setowner "SYSTEM" /t /c /l /q`)*.

### Vérification du succès

Exécutez la commande d'inspection pour valider que l'ancien compte ne figure plus dans les autorisations :
```cmd
icacls C:\Users\Default
```


## Script Batch pour automatiser le ModOp (Non testé)

```cmd
@echo off
echo ============================================================
echo   AUTOMATISATION WinRE : Remplacement du dossier Default
echo ============================================================
echo.

:: 1. DEFINITION DE LA VARIABLE USER
set "USER_MODELE=TEMP"

echo [*] Utilisateur modèle ciblé : %USER_MODELE%
echo.

if not exist "C:\Users\%USER_MODELE%" (
    echo [ERROR] Le dossier C:\Users\%USER_MODELE% n'existe pas sur C:.
    echo Vérifiez la lettre du lecteur ou le nom du dossier.
    pause
    exit /b
)

:: 2. SAUVEGARDE DU DOSSIER DEFAULT ACTUEL
echo [*] Sauvegarde du dossier Default d'origine...
takeown /f C:\Users\Default /a /r /d o > nul 2>&1
icacls C:\Users\Default /grant Administrateurs:F /t > nul 2>&1
attrib -h -s -r C:\Users\Default > nul 2>&1

if exist "C:\Users\Default.old" (
    rmdir /s /q C:\Users\Default.old
)
ren C:\Users\Default Default.old
echo [+] Dossier Default renommé en Default.old.

:: 3. COPIE DU PROFIL MODELE VERS DEFAULT
echo [*] Copie du profil %USER_MODELE% vers Default...
xcopy "C:\Users\%USER_MODELE%" "C:\Users\Default" /E /H /C /I /Y > nul

:: 4. NETTOYAGE DES PERMISSIONS NTFS ET PROPRIETE
echo [*] Reconfiguration des permissions et du propriétaire...
icacls C:\Users\Default /remove %USER_MODELE% /t /c /l /q > nul 2>&1
icacls C:\Users\Default /reset /t /c /l /q > nul 2>&1
icacls C:\Users\Default /grant Administrateurs:(OI)(CI)F /T > nul 2>&1
icacls C:\Users\Default /grant SYSTEM:(OI)(CI)F /T > nul 2>&1
icacls C:\Users\Default /grant Utilisateurs:(OI)(CI)RX /T > nul 2>&1
icacls C:\Users\Default /setowner "SYSTEM" /t /c /l /q > nul 2>&1

:: Réapplication des attributs Système et Caché
attrib +h +s C:\Users\Default
echo [+] Dossier C:\Users\Default configuré.

:: 5. SUPPRESSION DU DOSSIER SOURCE TEMPORAIRE
echo [*] Suppression du dossier C:\Users\%USER_MODELE%...
rmdir /s /q "C:\Users\%USER_MODELE%"
echo [+] Dossier source supprimé.

echo.
echo ============================================================
echo   TÂCHE WINRE TERMINEE !
echo   Note : Pensez à supprimer le compte %USER_MODELE% et
echo   sa clé dans le registre une fois Windows redémarré.
echo ============================================================
pause
```