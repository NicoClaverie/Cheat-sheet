# Cheat sheet commande windows


### Commandes Tiers


|   **Commandes**   |    **Action**     |
| :---------------: | :---------------: |
|     ``Win+R``     |     Exécuter      |
| ``mmc et ctrl+m`` | racine de console |


### Commandes système et gestion de l’ordinateur :


|       **Commandes**        |                         **Action**                          |
| :------------------------: | :---------------------------------------------------------: |
|      ``services.msc``      |             Ouvrir le gestionnaire de services.             |
|      ``taskschd.msc``      |             Accéder au planificateur de tâches.             |
|      ``diskmgmt.msc``      |              Gérer les partitions et disques.               |
|      ``devmgmt.msc``       |          Ouvrir le gestionnaire de périphériques.           |
|      ``compmgmt.msc``      |       Accéder aux outils de gestion de l’ordinateur.        |
|      ``wmimgmt.msc``       |                   Console de gestion WMI.                   |
|        ``msconfig``        |          Configurer le démarrage et les services.           |
|      ``perfmon.msc``       |             Lancer l’analyseur de performances.             |
|       ``secpol.msc``       |       Configurer les stratégies de sécurité locales.        |
|       ``gpedit.msc``       |           Gérer les stratégies de groupe locale.            |
|      ``lusrmgr.msc``       |          Gérer les utilisateurs et groupes locaux           |
|       `taskmgr.exe`        |             Gestionnaire des tâches de Windows              |
|     `gpupdate /force`      |             Force l'application des GPO de l'AD             |
| `gpresult /h c:\toto.html` |    Génère un fichier HTML qui contient les GPO appliqués    |
|        `fsmgmt.msc`        | Ouvre la fenêtre pour visualiser tout les dossiers partagés |
|     `optionalfeatures`     |            Ouvrir les fonctionnalités de Windows            |
|`wscui.cpl`|Ouvrir Sécurité et maintenance|


### Commandes pour les outils du Panneau de configuration :


|    **Commandes**    |               **Action**                |
| :-----------------: | :-------------------------------------: |
|`control.exe`|Ouvrir le panneau de configuration|
|   ``appwiz.cpl``    |     Gérer les programmes installés.     |
| ``control folders`` |    Accéder aux options de dossiers.     |
|    ``desk.cpl``     |         Configurer l’affichage.         |
|    ``intl.cpl``     | Paramètres régionaux et linguistiques.  |
|  ``timedate.cpl``   |       Régler l’heure et la date.        |
|    ``sysdm.cpl``    |     Ouvrir les propriétés système.      |
|  ``firewall.cpl``   |       Gérer le pare-feu Windows.        |
|  ``powercfg.cpl``   | Modifier les paramètres d’alimentation. |
|    ``mmsys.cpl``    |   Configurer les périphériques audio.   |
|`inetcpl.cpl`| Ouvrir propriété de Internet |


### Commandes réseau et connectivité :


|                  **Commandes**                   |                    **Action**                     |
| :----------------------------------------------: | :-----------------------------------------------: |
|                   ``ipconfig``                   |     Afficher et configurer les paramètres IP.     |
|                    ``wf.msc``                    | Gérer les paramètres avancés du pare-feu Windows. |
|                   ``ncpa.cpl``                   |          Accéder aux connexions réseau.           |
|                 ``virtmgmt.msc``                 |          Ouvrir le gestionnaire Hyper-V           |
|                   ``netplwiz``                   |      Gérer les utilisateurs et leurs accès.       |
|                ``ping [adresse]``                |         Vérifier la connectivité réseau.          |
|              ``tracert [adresse]``               |          Diagnostiquer le chemin réseau.          |
|           ``netsh wlan show profiles``           |       Lister les profils Wi-Fi enregistrés.       |
|           ``netsh winsock reset all``            |              Reset de la pile TCP-IP              |
| ``net use X: \\Serveur\Partage /persistent:yes`` |             Ajouter un lecteur réseau             |
|`%localappdata%\Diagnostics\Network`|Ouvre le journal de diagnostique réseau|


### Commandes pratiques pour les diagnostics et la productivité :


|           **Commandes**            |                          **Action**                          |
| :--------------------------------: | :----------------------------------------------------------: |
|             ``dxdiag``             |            Lancer l’outil de diagnostic DirectX.             |
|          ``eventvwr.msc``          |            Accéder à l’observateur d’événements.             |
|              ``cmd``               |                Ouvrir l’invite de commandes.                 |
|            ``regedit``             | Accéder à l’éditeur de registre (à manipuler avec prudence). |
|            ``cleanmgr``            |                 Ouvrir le netoyeur de l’espace disque.       |
|             ``chkdsk``             |          Vérifier et réparer les erreurs de disque.          |
|          ``sfc /scannow``          |           Scanner et réparer les fichiers système.           |
|          ``shutdown -s``           |                       Éteindre le PC.                        |
|          ``shutdown -r``           |                      Redémarrer le PC.                       |
|            ``verifier``            |              Diagnostiquer les pilotes système.              |
| `powercfg.exe /hibernate (off-on)` |          libère le cache pendant la mise en veille           |
|              `winver`              |          Permet de connaître la version de Windows           |
|`rundll32.exe dsquery.dll,OpenQueryWindow`|Rechercher utilisateurs, contacts et groupes de l'AD|
|`wmic bios get serialnumber`|Obtenir le numéro de série d'un pc|


### Commandes pour les outils intégrés Windows :


|  **Commandes**   |             **Action**             |
| :--------------: | :--------------------------------: |
|   ``notepad``    |       Ouvrir le Bloc-notes.        |
|   ``msinfo32``   | Obtenir des informations système.  |
|    ``mstsc``     |   Accéder au bureau à distance.    |
|     ``calc``     |      Ouvrir la calculatrice.       |
|   ``mspaint``    |           Lancer Paint.            |
| ``snippingtool`` | Lancer l’outil de capture d’écran. |
|   ``magnify``    |          Ouvrir la loupe.          |
|     ``osk``      |    Afficher le clavier visuel.     |
| `printbrmui.exe` | Utilitaire pour importer les imprimantes d'une machine et les exporter vers une autre machine |
|`resmon.exe`|Ouvrir le moniteur de ressource|


### Autres commandes utiles :


|     **Commandes**     |                       **Action**                       |
| :-------------------: | :----------------------------------------------------: |
|      ``%temp%``       |      Accéder au dossier des fichiers temporaires.      |
|   ``%userprofile%``   |       Ouvrir le dossier de l’utilisateur actif.        |
|     ``%windir%``      |              Accéder au dossier Windows.               |
|     ``explorer``      |           Lancer l’explorateur de fichiers.            |
|      ``syskey``       | Sécuriser la base de données des comptes utilisateurs. |
|      ``rstrui``       |            Lancer la restauration système.             |
| ``net stop spooler``  |                Arrêt spooler impression                |
| ``net start spooler`` |              Démarrage spooler impression              |


### Commandes PowerShell pour l'obtention d'information :

|     **Commandes**     |                       **Action**                       |
| :-------------------: | :----------------------------------------------------: |
|      `Get-WmiObject win32_bios \| select Serialnumber` ou `Get-ComputerInfo -Property "Biosseralnumber"`     |      Permet d'obtenir le numéro de série de la carte mère      |


