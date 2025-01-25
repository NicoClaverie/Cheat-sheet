# Liste des principaux statuts HTTP et ce qu’ils signifient :  

### 1xx - Information en route :  
Les serveurs disent : “J’ai bien reçu ta demande, attends un peu, je bosse dessus…”  
- 100 Continue : “Tout roule, continue ce que tu fais !”  

### 2xx - Tout est OK :  
Le serveur te dit : “Mission accomplie, tout va bien !”  
- 200 OK : “Ta demande est un succès, voici ton contenu !”  
- 201 Created : “Bravo, tu as créé quelque chose de nouveau !”  
- 204 No Content : “J’ai fait ce que tu voulais, mais j’ai rien à te montrer.”  

### 3xx - Faut changer de route :  
Le serveur te dit : “Heu… regarde ailleurs, ce que tu cherches n’est plus ici.”  
- 301 Moved Permanently : “La boîte a déménagé.”  
- 302 Found : “C’est ici pour l’instant, mais ça pourrait changer.”  
- 304 Not Modified : “Pas besoin de retélécharger, c’est toujours bon !”  

### 4xx - C’est ta faute :  
Le serveur râle : “Non, ce que tu fais n’est pas bon.”  
- 400 Bad Request : “Ta demande est bizarre, reformule !”   
- 401 Unauthorized : “T’as pas les clés.”  
- 403 Forbidden : “Même avec des clés, tu n’entres pas ici !”  
- 404 Not Found : “Rien à voir ici, cherche ailleurs.”  
- 418 I'm a teapot : "le serveur refuse de préparer du café, car il s'agit d'une théière"  

### 5xx - Le serveur crame :  
Le serveur s’excuse : “Oups, j’ai un problème de mon côté !”  
- 500 Internal Server Error : “Un truc est cassé, on panique.”  
- 502 Bad Gateway : “Le voisin m’a donné une mauvaise réponse.”  
- 503 Service Unavailable : “Je suis en pause café, reviens plus tard.”  
