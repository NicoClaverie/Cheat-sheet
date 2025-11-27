# Liste de REG interessant pour Windows

## Rendre le démarrage verbeux

Pratique si on veux savoir ce qu'il se passe lors du démarrage ou l'arret de la machine.

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System]
"verbosestatus"=dword:00000001
```

## Désactiver le MPO

Active un mode de test (OverlayTestMode=5) pour le Desktop Window Manager (DWM), qui gère le rendu et les superpositions graphiques du bureau Windows.  
Pratique pour le probleme de souris qui reste blanche sur une zone de texte.

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Dwm]
"OverlayTestMode"=dword:00000005
```
