C'est une excellente trouvaille. La Sysinternals Suite (créée par Mark Russinovich, aujourd'hui CTO d'Azure) est considérée comme la "boîte à outils ultime" pour tout administrateur système ou utilisateur avancé sur Windows.

La suite contient plus de 70 utilitaires. Il serait trop long de tous les détailler individuellement ici, mais je vais te présenter les plus importants et les plus puissants, classés par catégorie, avec des exemples concrets d'utilisation.

Voici le guide détaillé des outils indispensables de la suite :

1. Les Incontournables (Le "Top 3")
Ce sont les outils à maîtriser absolument pour le dépannage.

Process Explorer (procexp.exe)
C'est un "Gestionnaire des tâches" sous stéroïdes. Il montre l'arborescence des processus (qui a lancé qui), les DLLs chargées et les handles (fichiers ouverts).

À quoi ça sert : Identifier les malwares, comprendre pourquoi un ordinateur est lent, ou voir quel programme verrouille un fichier.

Exemple : Tu essaies de supprimer un fichier mais Windows dit "Fichier utilisé par un autre processus".

Action : Ouvre Process Explorer > Find > Find Handle or DLL > Tape le nom du fichier. Il te dira exactement quel programme le bloque. Tu peux alors fermer le programme ou fermer le "handle" directement.

Process Monitor (procmon.exe)
L'outil de diagnostic ultime. Il enregistre en temps réel toutes les activités du système de fichiers, du registre et des processus.

À quoi ça sert : Comprendre pourquoi une application plante, ne démarre pas, ou où elle stocke ses paramètres.

Exemple : Un logiciel affiche une erreur "Accès refusé" au démarrage.

Action : Lance ProcMon, reproduis l'erreur, et arrête la capture. Filtre par "Result: ACCESS DENIED". Tu verras immédiatement quel fichier ou clé de registre le logiciel essayait de toucher sans en avoir le droit.

Autoruns (autoruns.exe)
Il voit tout ce qui se lance au démarrage de Windows (bien plus que l'onglet "Démarrage" du gestionnaire des tâches). Il vérifie les services, les tâches planifiées, les extensions de l'explorateur, etc.

À quoi ça sert : Optimiser le démarrage et supprimer les persistanes de virus.

Exemple : Ton PC est lent au démarrage ou des pubs s'ouvrent seules.

Action : Lance Autoruns en administrateur. Regarde les lignes surlignées en rose (pas de signature numérique) ou jaune (fichier introuvable). Décoche la case pour désactiver l'élément suspect.

2. La suite PsTools (Ligne de commande & Réseau)
Ces outils s'utilisent dans l'invite de commande (cmd ou PowerShell). Ils permettent souvent d'agir sur des PC distants.

PsExec (psexec.exe)
Le plus célèbre. Il permet d'exécuter des commandes sur une machine distante sans installer de logiciel client, ou de lancer des processus en tant qu'utilisateur "SYSTÈME".

Exemple distant : Tu veux lancer une mise à jour (update.exe) sur un serveur distant sans t'y connecter en RDP.

psexec \\nom_serveur -u administrateur -p motdepasse c:\temp\update.exe

Exemple local (Hack) : Tu veux ouvrir une invite de commande avec les droits absolus (SYSTEM) pour tuer un processus système.

psexec -i -s cmd.exe

PsKill (pskill.exe)
Tue des processus, même à distance.

Exemple : Un logiciel a planté sur le PC d'un collègue nommé "PC-COMPTA".

pskill \\PC-COMPTA excel.exe

PsList (pslist.exe)
Affiche les processus et leurs statistiques (mémoire, CPU).

Exemple : Surveiller l'usage CPU d'un serveur à distance.

PsLoggedOn (psloggedon.exe)
Affiche qui est connecté sur une machine (localement ou via des partages réseaux).

Exemple : Savoir qui utilise le serveur de fichiers en ce moment.

3. Réseau et Sécurité
TCPView (tcpview.exe)
Une version graphique de la commande netstat. Il montre toutes les connexions TCP et UDP actives et quel processus les utilise.

Exemple : Ton internet est lent. Tu ouvres TCPView et tu vois qu'un processus inconnu (malware.exe) envoie des données vers une IP en Russie. Tu peux faire clic-droit > "Close Connection" ou "End Process".

AccessChk (accesschk.exe)
Vérifie les permissions (droits d'accès) sur des fichiers, clés de registre ou services.

Exemple : Vérifier si le groupe "Utilisateurs" a le droit d'écrire dans le dossier C:\Program Files\MonAppli.

accesschk "Users" c:\Program Files\MonAppli

Sysmon (sysmon.exe)
Un outil de surveillance avancé qui s'installe comme service et écrit dans le journal d'événements Windows. Très utilisé par les experts en cybersécurité pour détecter des intrusions.

Exemple : Il peut loguer chaque fois qu'un processus lance un autre processus (ex: Word qui lance PowerShell = virus probable), incluant la ligne de commande exacte utilisée.

4. Disques et Fichiers
Disk Usage (du.exe)
Affiche l'utilisation disque par répertoire (en ligne de commande).

Exemple : Trouver quel sous-dossier prend toute la place sur le serveur.

du -v c:\users

SDelete (sdelete.exe)
Suppression sécurisée (norme militaire). Il écrase l'espace libre ou un fichier spécifique pour empêcher la récupération de données.

Exemple : Tu vends ton PC et tu veux être sûr que personne ne récupère tes vieux fichiers supprimés.

sdelete -z c: (Nettoie l'espace libre du disque C).

Contig (contig.exe)
Défragmente un fichier spécifique (au lieu de tout le disque).

Exemple : Optimiser le fichier d'une base de données SQL ou une machine virtuelle qui est devenu lent.

5. Utilitaires Système / Divers
BgInfo (bginfo.exe)
Génère une image de fond d'écran contenant des infos techniques (Nom du PC, IP, OS, RAM, Espace disque).

Exemple : Très utilisé sur les serveurs pour qu'un administrateur sache immédiatement sur quelle machine il est connecté en ouvrant sa session.

ZoomIt (zoomit.exe)
Outil de présentation. Permet de zoomer sur l'écran et de dessiner dessus avec des raccourcis clavier.

Exemple : Utile si tu fais une présentation sur projecteur et que tu veux montrer un détail dans une interface complexe. (Ctrl+1 pour zoomer, Ctrl+2 pour dessiner).

Desktops (desktops.exe)
Permet de créer jusqu'à 4 bureaux virtuels (avant que Windows 10 ne l'intègre nativement, mais fonctionne différemment techniquement).

Strings (strings.exe)
Scanne un fichier binaire (exe, dll) et affiche tout le texte lisible (ASCII/Unicode) qu'il trouve dedans.

Exemple : Analyser un fichier suspect pour voir s'il contient des URLs ou des messages d'erreur cachés sans l'exécuter.

Résumé pour bien débuter
Si tu ne dois en retenir que trois :

Process Explorer (remplace ton gestionnaire des tâches).

Autoruns (nettoie ton démarrage).

TCPView (surveille ton réseau).

Attention : Ces outils sont puissants. SDelete ou PsKill mal utilisés peuvent faire perdre des données.

Souhaites-tu un tutoriel plus approfondi sur l'un de ces outils en particulier ?
