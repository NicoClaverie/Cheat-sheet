# Cheat Sheet des commandes python ( EN COURS )


🐍 Cheat Sheet Python — Méthodes des objets standards

🧩 Listes (list):

|             Méthode              |                        Description                         |
| :------------------------------: | :--------------------------------------------------------: |
|           `.append(x)`           |           Ajoute un élément à la fin de la liste           |
|       `.extend(iterable)`        |  Ajoute les éléments d’un autre itérable (liste, tuple…)   |
|         `.insert(i, x)`          |                  Insère x à la position i                  |
|           `.remove(x)`           |            Supprime la première occurrence de x            |
|           `.pop([i])`            | Supprime et renvoie l’élément à l’indice i (ou le dernier) |
|            `.clear()`            |                       Vide la liste                        |
|   `.index(x[, start[, end]])`    |      Renvoie l’indice de la première occurrence de x       |
|           `.count(x)`            |            Compte le nombre d’occurrences de x             |
| `.sort(key=None, reverse=False)` |                   Trie la liste en place                   |
|           `.reverse()`           |                Inverse l’ordre des éléments                |
|            `.copy()`             |        Retourne une copie superficielle de la liste        |

🧵 Chaînes de caractères (str) :

|                 Méthode                 |                             Description                              |
| :-------------------------------------: | :------------------------------------------------------------------: |
|             `.capitalize()`             |                 Met la première lettre en majuscule                  |
|              `.casefold()`              |         Convertit en minuscules (plus agressif que .lower())         |
|      `.center(width[, fillchar])`       |                           Centre le texte                            |
|      `.count(sub[, start[, end]])`      |               Compte les occurrences d’une sous-chaîne               |
|   `.endswith(suffix[, start[, end]])`   |              Vérifie si la chaîne se termine par suffix              |
|      `.find(sub[, start[, end]])`       |             Renvoie l’indice de sub ou -1 si non trouvé              |
|      `.index(sub[, start[, end]])`      |           Comme .find() mais lève une erreur si non trouvé           |
|            `.join(iterable)`            | Concatène les éléments d’un itérable avec la chaîne comme séparateur |
|               `.lower()`                |                        Met tout en minuscules                        |
|               `.upper()`                |                        Met tout en majuscules                        |
|      `.replace(old, new[, count])`      |                      Remplace des sous-chaînes                       |
|     `.split(sep=None, maxsplit=-1)`     |                 Découpe en liste selon un séparateur                 |
|        `.splitlines([keepends])`        |                    Découpe sur les sauts de ligne                    |
|  `.startswith(prefix[, start[, end]])`  |               Vérifie si la chaîne commence par prefix               |
|            `.strip([chars])`            |          Supprime les espaces ou caractères en début et fin          |
| `.rstrip([chars])` / `.lstrip([chars])` |                       Supprime à droite/gauche                       |
|               `.title()`                |                     Met chaque mot en majuscule                      |
|             `.zfill(width)`             |        Ajoute des zéros en début jusqu’à atteindre la largeur        |

📘 Dictionnaires (dict):

|           Méthode           |                     Description                      |
| :-------------------------: | :--------------------------------------------------: |
|          .clear()           |                 Vide le dictionnaire                 |
|           .copy()           |                 Copie superficielle                  |
|    .get(key[, default])     |       Récupère une valeur sans lever d’erreur        |
|          .items()           |          Retourne les paires (clé, valeur)           |
|           .keys()           |                  Retourne les clés                   |
|          .values()          |                 Retourne les valeurs                 |
|    .pop(key[, default])     |        Supprime et renvoie la valeur associée        |
|         .popitem()          | Supprime et renvoie une paire clé/valeur arbitraire  |
| .setdefault(key[, default]) |    Renvoie la valeur associée ou crée une entrée     |
|      .update([other])       | Met à jour à partir d’un autre dict ou d’un itérable |

🔘 Ensembles (set et frozenset)

|                Méthode                |                  Description                  |
| :-----------------------------------: | :-------------------------------------------: |
|              .add(elem)               |               Ajoute un élément               |
|               .clear()                |                Vide l’ensemble                |
|                .copy()                |              Copie superficielle              |
|         .difference(other, …)         |            Différence d’ensembles             |
|     .difference_update(other, …)      | Met à jour en supprimant les éléments communs |
|            .discard(elem)             |        Supprime sans erreur si absent         |
|        .intersection(other, …)        |                 Intersection                  |
|    .intersection_update(other, …)     |        Met à jour avec l’intersection         |
|          .isdisjoint(other)           |   Teste s’il n’y a aucun élément en commun    |
| .issubset(other) / .issuperset(other) |                Teste inclusion                |
|                .pop()                 |        Supprime un élément arbitraire         |
|             .remove(elem)             |     Supprime un élément, erreur si absent     |
|     .symmetric_difference(other)      |             Différence symétrique             |
|           .union(other, …)            |              Union des ensembles              |
|           .update(other, …)           |           Ajoute plusieurs éléments           |

🧮 Tuples (tuple)

Les tuples sont immuables, donc très peu de méthodes :

|  Méthode  |           Description            |
| :-------: | :------------------------------: |
| .count(x) |       Nombre d’occurrences       |
| .index(x) | Indice de la première occurrence |

📁 Fichiers (file object)

|         Méthode         |             Description              |
| :---------------------: | :----------------------------------: |
|        .close()         |           Ferme le fichier           |
|      .read([size])      |            Lit le contenu            |
|    .readline([size])    |            Lit une ligne             |
|   .readlines([hint])    | Lit toutes les lignes dans une liste |
|        .write(s)        |           Écrit une chaîne           |
|   .writelines(lines)    |      Écrit une liste de chaînes      |
| .seek(offset[, whence]) |    Change la position du curseur     |
|         .tell()         |      Donne la position actuelle      |
|        .flush()         |   Force l’écriture dans le fichier   |
|    .truncate([size])    |          Tronque le fichier          |

🔢 Objets divers utiles

|             Méthode / Fonction             |  Type   |              Description               |
| :----------------------------------------: | :-----: | :------------------------------------: |
|                 .format()                  |   str   |          Formatage de chaînes          |
|       .enumerate(iterable, start=0)        | builtin |           Énumère avec index           |
|              .zip(*iterables)              | builtin |      Combine plusieurs itérables       |
|            .map(func, iterable)            | builtin | Applique une fonction à chaque élément |
|          .filter(func, iterable)           | builtin |       Filtre selon une condition       |
| .sorted(iterable, key=None, reverse=False) | builtin |     Trie sans modifier l’original      |


⚙️ Fonctions intégrées Python (builtins)

|                      Fonction                       |                        Description                         |
| :-------------------------------------------------: | :--------------------------------------------------------: |
|                       abs(x)                        |                       Valeur absolue                       |
|                    all(iterable)                    |      Retourne `True` si tous les éléments sont vrais       |
|                    any(iterable)                    |      Retourne `True` si au moins un élément est vrai       |
|                     ascii(obj)                      |         Retourne une version imprimable de l’objet         |
|                       bin(x)                        |          Convertit un entier en binaire ('0b...')          |
|                       bool(x)                       |                    Convertit en booléen                    |
|                    breakpoint()                     |                 Lance le débogueur intégré                 |
|        bytearray([source]) / bytes([source])        |                   Crée des objets bytes                    |
|                    callable(obj)                    | Vérifie si un objet est appelable (fonction, classe, etc.) |
|                       chr(i)                        |           Convertit un code Unicode en caractère           |
|                  classmethod(func)                  |               Définit une méthode de classe                |
|           compile(source, filename, mode)           |                   Compile du code source                   |
|                complex(real[, imag])                |                  Crée un nombre complexe                   |
|                 delattr(obj, name)                  |                    Supprime un attribut                    |
|                       dict()                        |                    Crée un dictionnaire                    |
|                     dir([obj])                      |               Liste les attributs d’un objet               |
|                    divmod(a, b)                     |                 Retourne (quotient, reste)                 |
|            enumerate(iterable, start=0)             |           Retourne un itérateur (index, valeur)            |
|        eval(expression[, globals[, locals]])        |                Évalue une expression Python                |
|          exec(object[, globals[, locals]])          |                   Exécute du code Python                   |
|               filter(func, iterable)                |               Filtre les éléments selon func               |
|                      float(x)                       |          Convertit en nombre à virgule flottante           |
|            format(value[, format_spec])             |                     Formate une valeur                     |
|                frozenset([iterable])                |                 Crée un ensemble immuable                  |
|            getattr(obj, name[, default])            |             Récupère un attribut dynamiquement             |
|                      globals()                      |              Retourne le dictionnaire global               |
|                 hasattr(obj, name)                  |             Vérifie si un objet a un attribut              |
|                      hash(obj)                      |                Retourne le hash d’un objet                 |
|                     help([obj])                     |                  Affiche l’aide intégrée                   |
|                       hex(x)                        |             Convertit un entier en hexadécimal             |
|                       id(obj)                       |          Retourne l’identifiant unique d’un objet          |
|                   input([prompt])                   |                 Lit une entrée utilisateur                 |
|                   int(x[, base])                    |                    Convertit en entier                     |
|             isinstance(obj, classinfo)              |                 Vérifie le type d’un objet                 |
|             issubclass(cls, classinfo)              |          Vérifie si une classe hérite d’une autre          |
|                iter(obj[, sentinel])                |                     Crée un itérateur                      |
|                      len(obj)                       |                    Longueur d’un objet                     |
|                  list([iterable])                   |                       Crée une liste                       |
|                      locals()                       |       Retourne le dictionnaire des variables locales       |
|               map(func, iterable, …)                |           Applique une fonction à chaque élément           |
|          max(iterable, *[, key, default])           |                      Élément maximum                       |
|          min(iterable, *[, key, default])           |                      Élément minimum                       |
|              next(iterator[, default])              |                 Renvoie l’élément suivant                  |
|                      object()                       |                 Crée un nouvel objet vide                  |
|                       oct(x)                        |                Convertit un entier en octal                |
|              open(file, mode='r', ...)              |                      Ouvre un fichier                      |
|                       ord(c)                        |           Convertit un caractère en code Unicode           |
|                   pow(x, y[, z])                    |           Exponentiation, ou modulo exponentiel            |
| print(*objects, sep=' ', end='\n', file=sys.stdout) |                      Affiche du texte                      |
| property(fget=None, fset=None, fdel=None, doc=None) |                  Crée une propriété (OOP)                  |
|             range(start, stop[, step])              |               Génère une séquence d’entiers                |
|                      repr(obj)                      |            Représentation officielle de l’objet            |
|                    reversed(seq)                    |                     Itérateur inversé                      |
|              round(number[, ndigits])               |                     Arrondit un nombre                     |
|                   set([iterable])                   |                      Crée un ensemble                      |
|              setattr(obj, name, value)              |                    Modifie un attribut                     |
|             slice(start, stop[, step])              |                     Objet de découpage                     |
|      sorted(iterable, key=None, reverse=False)      |               Trie sans modifier l’original                |
|                 staticmethod(func)                  |                Définit une méthode statique                |
|                   str(object='')                    |                    Convertit en chaîne                     |
|               sum(iterable[, start])                |                     Somme des éléments                     |
|           super([type[, object-or-type]])           |                 Appelle la classe parente                  |
|                  tuple([iterable])                  |                       Crée un tuple                        |
|                      type(obj)                      |                  Donne le type de l’objet                  |
|                     vars([obj])                     |         Retourne les attributs sous forme de dict          |
|                   zip(*iterables)                   |                Combine plusieurs itérables                 |
|                  __import__(name)                   |                 Fonction d’import interne                  |
|           .any(iterable) / .all(iterable)           |            builtin	Vérifie conditions logiques             |
|               .sum(iterable[, start])               |                   builtin	Fait la somme                    |
|                   .min() / .max()                   |            builtin	Valeur minimale ou maximale             |


🧙‍♂️ Méthodes spéciales Python (dunder methods)

Les “dunder” (de double underscore) sont des méthodes magiques appelées automatiquement par Python.
Elles commencent et finissent par __, comme __init__.

⚙️ Méthodes de base des objets

|            Méthode            |        Appelée quand…        |         Exemple / Utilité         |
| :---------------------------: | :--------------------------: | :-------------------------------: |
|       __init__(self, …)       |     Création d’un objet      |     Initialise les attributs      |
|         __del__(self)         |    Destruction de l’objet    |    Nettoyage avant suppression    |
|        __repr__(self)         |  Représentation officielle   | repr(obj) ou affichage en console |
|         __str__(self)         | Conversion en chaîne lisible |      str(obj) ou print(obj)       |
|        __bytes__(self)        |     Conversion en bytes      |            bytes(obj)             |
| __format__(self, format_spec) |    Formatage personnalisé    |        format(obj, "spec")        |
|        __hash__(self)         |       Hash d’un objet        |   Utilisé dans les set et dict    |
|      __eq__(self, other)      |        Comparaison ==        |          Test d’égalité           |
|      __ne__(self, other)      |        Comparaison !=        |        Test de différence         |
|      __lt__(self, other)      |        Comparaison <         |      Ordre strict inférieur       |
|      __le__(self, other)      |        Comparaison <=        |      Ordre inférieur ou égal      |
|      __gt__(self, other)      |        Comparaison >         |      Ordre strict supérieur       |
|      __ge__(self, other)      |        Comparaison >=        |      Ordre supérieur ou égal      |

📦 Méthodes liées aux conteneurs (listes, dicts, etc.)

|            Méthode            |  Appelée quand…  |      Exemple / Utilité      |
| :---------------------------: | :--------------: | :-------------------------: |
|         __len__(self)         |     len(obj)     |     Taille ou longueur      |
|    __getitem__(self, key)     |     obj[key]     |     Accès à un élément      |
| __setitem__(self, key, value) | obj[key] = value |         Affectation         |
|    __delitem__(self, key)     |   del obj[key]   |         Suppression         |
|        __iter__(self)         |    Boucle for    |    Rend l’objet itérable    |
|        __next__(self)         |    next(obj)     | Élément suivant (itérateur) |
|   __contains__(self, item)    |   item in obj    |     Vérifie la présence     |
|      __reversed__(self)       |  reversed(obj)   |      Inversion d’ordre      |

➕ Méthodes arithmétiques

|          Méthode          |    Opération     |   Exemple   |
| :-----------------------: | :--------------: | :---------: |
|  ` __add__(self, other)`  |     Addition     |    a + b    |
|   __sub__(self, other)    |   Soustraction   |    a - b    |
|   __mul__(self, other)    |  Multiplication  |    a * b    |
| __truediv__(self, other)  | Division réelle  |    a / b    |
| __floordiv__(self, other) | Division entière |   a // b    |
|   __mod__(self, other)    |      Modulo      |    a % b    |
|   __pow__(self, other)    |    Puissance     |   a ** b    |
|       __neg__(self)       |     Négation     |     -a      |
|       __pos__(self)       |  Signe positif   |     +a      |
|       __abs__(self)       |  Valeur absolue  |   abs(a)    |
|    __round__(self, n)     |     Arrondi      | round(a, n) |

🔁 Méthodes d’assignation arithmétique (in-place)

|          Méthode           |         Opération         | Exemple |
| :------------------------: | :-----------------------: | :-----: |
|   __iadd__(self, other)    |     Addition en place     | a += b  |
|   __isub__(self, other)    |   Soustraction en place   | a -= b  |
|   __imul__(self, other)    |  Multiplication en place  | a *= b  |
| __itruediv__(self, other)  |     Division en place     | a /= b  |
| __ifloordiv__(self, other) | Division entière en place | a //= b |
|   __imod__(self, other)    |      Modulo en place      | a %= b  |

🔤 Méthodes de gestion des attributs

|            Méthode             |          Appelée quand…           |     Exemple / Utilité      |
| :----------------------------: | :-------------------------------: | :------------------------: |
|    __getattr__(self, name)     |  Accès à un attribut inexistant   |     Gestion dynamique      |
|  __getattribute__(self, name)  |       Accès à tout attribut       |   Interception complète    |
| __setattr__(self, name, value) |      Affectation d’attribut       | Contrôle de la mise à jour |
|    __delattr__(self, name)     |      Suppression d’attribut       |        del obj.attr        |
|     __dir__(self)	dir(obj)     | Liste des attributs personnalisée |

🧠 Autres méthodes spéciales utiles

|                           Méthode                           |               Appelée quand…                | Exemple / Utilité |
| :---------------------------------------------------------: | :-----------------------------------------: | :---------------: |
|                      __call__(self, …)                      | Quand l’objet est appelé comme une fonction |       obj()       |
| __enter__(self) / __exit__(self, exc_type, exc_val, exc_tb) |       Gestionnaire de contexte (with)       |     with obj:     |
|          __copy__(self) / __deepcopy__(self, memo)          |        Copie d’objets personnalisée         |  copy.copy(obj)   |
|                       __bool__(self)                        |            Conversion booléenne             |      if obj:      |
|                       __index__(self)                       |            Conversion en entier             |     hex(obj)      |
|                __class_getitem__(cls, item)                 |       Typage générique (Python 3.9+)        |   MyClass[int]    |



# 🐍 Cheat Sheet Python — Méthodes, Fonctions et Dunder

## 🧩 Listes (`list`)
| Méthode                          | Description                                  |
| -------------------------------- | -------------------------------------------- |
| `.append(x)`                     | Ajoute un élément à la fin de la liste       |
| `.extend(iterable)`              | Ajoute les éléments d’un autre itérable      |
| `.insert(i, x)`                  | Insère `x` à la position `i`                 |
| `.remove(x)`                     | Supprime la première occurrence de `x`       |
| `.pop([i])`                      | Supprime et renvoie l’élément à l’indice `i` |
| `.clear()`                       | Vide la liste                                |
| `.index(x[, start[, end]])`      | Renvoie l’indice de `x`                      |
| `.count(x)`                      | Compte le nombre d’occurrences               |
| `.sort(key=None, reverse=False)` | Trie la liste en place                       |
| `.reverse()`                     | Inverse l’ordre                              |
| `.copy()`                        | Copie superficielle                          |

---

## 🧵 Chaînes de caractères (`str`)
| Méthode                               | Description                               |
| ------------------------------------- | ----------------------------------------- |
| `.capitalize()`                       | Première lettre en majuscule              |
| `.casefold()`                         | Minuscules agressives                     |
| `.center(width[, fillchar])`          | Centre le texte                           |
| `.count(sub[, start[, end]])`         | Compte les occurrences                    |
| `.endswith(suffix[, start[, end]])`   | Teste la fin                              |
| `.find(sub[, start[, end]])`          | Trouve une sous-chaîne                    |
| `.index(sub[, start[, end]])`         | Comme `.find()` mais erreur si non trouvé |
| `.join(iterable)`                     | Concatène un itérable                     |
| `.lower()` / `.upper()`               | Minuscules / majuscules                   |
| `.replace(old, new[, count])`         | Remplace des sous-chaînes                 |
| `.split(sep=None, maxsplit=-1)`       | Découpe en liste                          |
| `.strip([chars])`                     | Supprime les espaces autour               |
| `.startswith(prefix[, start[, end]])` | Teste le début                            |
| `.zfill(width)`                       | Ajoute des zéros devant                   |

---

## 📘 Dictionnaires (`dict`)
| Méthode                       | Description                  |
| ----------------------------- | ---------------------------- |
| `.clear()`                    | Vide le dictionnaire         |
| `.copy()`                     | Copie superficielle          |
| `.get(key[, default])`        | Récupère une valeur          |
| `.items()`                    | Liste les paires clé/valeur  |
| `.keys()`                     | Liste les clés               |
| `.values()`                   | Liste les valeurs            |
| `.pop(key[, default])`        | Supprime une clé             |
| `.popitem()`                  | Supprime une paire aléatoire |
| `.setdefault(key[, default])` | Valeur par défaut            |
| `.update([other])`            | Fusionne avec un autre dict  |

---

## 🔘 Ensembles (`set`)
| Méthode                                   | Description               |
| ----------------------------------------- | ------------------------- |
| `.add(elem)`                              | Ajoute un élément         |
| `.clear()`                                | Vide l’ensemble           |
| `.copy()`                                 | Copie superficielle       |
| `.difference(other, …)`                   | Différence                |
| `.intersection(other, …)`                 | Intersection              |
| `.union(other, …)`                        | Union                     |
| `.isdisjoint(other)`                      | Aucun élément commun      |
| `.issubset(other)` / `.issuperset(other)` | Teste inclusion           |
| `.remove(elem)` / `.discard(elem)`        | Supprime un élément       |
| `.update(other, …)`                       | Ajoute plusieurs éléments |

---

## 🧮 Tuples (`tuple`)
| Méthode     | Description                      |
| ----------- | -------------------------------- |
| `.count(x)` | Nombre d’occurrences             |
| `.index(x)` | Indice de la première occurrence |

---

## 📁 Fichiers (`file`)
| Méthode                   | Description            |
| ------------------------- | ---------------------- |
| `.close()`                | Ferme le fichier       |
| `.read([size])`           | Lit le contenu         |
| `.readline([size])`       | Lit une ligne          |
| `.readlines([hint])`      | Liste des lignes       |
| `.write(s)`               | Écrit une chaîne       |
| `.writelines(lines)`      | Écrit plusieurs lignes |
| `.seek(offset[, whence])` | Change la position     |
| `.tell()`                 | Donne la position      |
| `.flush()`                | Force l’écriture       |

---

## ⚙️ Fonctions intégrées Python (*builtins*)
| Fonction                                           | Description                      |
| -------------------------------------------------- | -------------------------------- |
| `abs(x)`                                           | Valeur absolue                   |
| `all(iterable)` / `any(iterable)`                  | Tous / au moins un élément vrai  |
| `bin(x)` / `hex(x)` / `oct(x)`                     | Conversion binaire / hex / octal |
| `bool(x)`                                          | Convertit en booléen             |
| `callable(obj)`                                    | Teste si appelable               |
| `chr(i)` / `ord(c)`                                | Code Unicode ↔ caractère         |
| `dict()`, `list()`, `tuple()`, `set()`             | Création d’objets standards      |
| `enumerate(iterable, start=0)`                     | Itère avec index                 |
| `filter(func, iterable)` / `map(func, iterable)`   | Filtrage / transformation        |
| `getattr(obj, name[, default])`                    | Récupère un attribut             |
| `hasattr(obj, name)` / `setattr(obj, name, value)` | Vérifie / modifie un attribut    |
| `id(obj)` / `type(obj)`                            | Identifiant / type               |
| `input([prompt])`                                  | Lecture utilisateur              |
| `isinstance(obj, cls)` / `issubclass(cls, base)`   | Vérifie le type                  |
| `len(obj)`                                         | Longueur                         |
| `max()` / `min()` / `sum()`                        | Valeur extrême / somme           |
| `next(iterator[, default])`                        | Élément suivant                  |
| `open(file, mode)`                                 | Ouvre un fichier                 |
| `print(*objects)`                                  | Affiche du texte                 |
| `range(start, stop[, step])`                       | Génère une séquence              |
| `repr(obj)` / `str(obj)`                           | Représentation texte             |
| `reversed(seq)`                                    | Inversé                          |
| `round(number[, ndigits])`                         | Arrondit                         |
| `sorted(iterable, key=None, reverse=False)`        | Trie                             |
| `zip(*iterables)`                                  | Combine plusieurs itérables      |

---

## 🧙‍♂️ Méthodes spéciales (*dunder methods*)
### ⚙️ Méthodes de base
| Méthode                                | Appelée quand…       | Exemple                     |
| -------------------------------------- | -------------------- | --------------------------- |
| `__init__`                             | Création d’objet     | Initialisation              |
| `__repr__` / `__str__`                 | Affichage            | `repr(obj)` / `print(obj)`  |
| `__eq__`, `__ne__`, `__lt__`, `__gt__` | Comparaisons         | `a == b`, `a < b`           |
| `__len__`                              | Longueur             | `len(obj)`                  |
| `__hash__`                             | Hash                 | Utilisé dans `set` / `dict` |
| `__bool__`                             | Conversion booléenne | `if obj:`                   |
| `__call__`                             | Appel comme fonction | `obj()`                     |

### 📦 Conteneurs
| Méthode                                     | Appelée quand…                    |
| ------------------------------------------- | --------------------------------- |
| `__getitem__`, `__setitem__`, `__delitem__` | Accès / affectation / suppression |
| `__iter__`, `__next__`                      | Itération                         |
| `__contains__`                              | `in`                              |
| `__reversed__`                              | `reversed(obj)`                   |

### ➕ Arithmétique
| Méthode                                        | Opération                         |
| ---------------------------------------------- | --------------------------------- |
| `__add__`, `__sub__`, `__mul__`, `__truediv__` | `+`, `-`, `*`, `/`                |
| `__floordiv__`, `__mod__`, `__pow__`           | `//`, `%`, `**`                   |
| `__iadd__`, `__isub__`, etc.                   | Opérations en place (`+=`)        |
| `__neg__`, `__abs__`, `__round__`              | Négation, valeur absolue, arrondi |

### 🔤 Attributs & contexte
| Méthode                                     | Appelée quand…        |
| ------------------------------------------- | --------------------- |
| `__getattr__`, `__setattr__`, `__delattr__` | Gestion des attributs |
| `__enter__`, `__exit__`                     | Bloc `with`           |
| `__copy__`, `__deepcopy__`                  | Copie personnalisée   |
| `__index__`                                 | Conversion en entier  |

---

# 🧰 Cheat Sheet Python — Modules Standard (Version Avancée)

## 📂 Module `os` — Interactions avec le système d’exploitation

| Fonction / Attribut                                   | Description                                |
| ----------------------------------------------------- | ------------------------------------------ |
| `os.name`                                             | Nom du système (`'posix'`, `'nt'`, etc.)   |
| `os.getcwd()`                                         | Renvoie le répertoire courant              |
| `os.chdir(path)`                                      | Change de répertoire                       |
| `os.listdir(path='.')`                                | Liste les fichiers d’un dossier            |
| `os.mkdir(path)` / `os.makedirs(path, exist_ok=True)` | Crée un dossier                            |
| `os.remove(path)`                                     | Supprime un fichier                        |
| `os.rmdir(path)` / `os.removedirs(path)`              | Supprime un dossier                        |
| `os.rename(src, dst)`                                 | Renomme un fichier                         |
| `os.stat(path)`                                       | Informations sur un fichier                |
| `os.path`                                             | Sous-module pour manipuler les chemins     |
| `os.environ`                                          | Dictionnaire des variables d’environnement |
| `os.system(cmd)`                                      | Exécute une commande système               |
| `os.cpu_count()`                                      | Nombre de cœurs du CPU                     |
| `os.getlogin()` / `os.getpid()`                       | Utilisateur / PID actuel                   |

---

## 🪶 Module `pathlib` — Gestion moderne des chemins

| Méthode / Attribut                          | Description                                |
| ------------------------------------------- | ------------------------------------------ |
| `Path.cwd()`                                | Répertoire courant                         |
| `Path.home()`                               | Dossier utilisateur                        |
| `Path('chemin')`                            | Crée un objet chemin                       |
| `p.exists()` / `p.is_file()` / `p.is_dir()` | Vérifie le type                            |
| `p.iterdir()`                               | Liste le contenu                           |
| `p.mkdir(parents=True, exist_ok=True)`      | Crée un dossier                            |
| `p.rename(nouveau_nom)`                     | Renomme                                    |
| `p.unlink()`                                | Supprime un fichier                        |
| `p.read_text()` / `p.write_text(data)`      | Lecture / écriture texte                   |
| `p.read_bytes()` / `p.write_bytes(data)`    | Lecture / écriture binaire                 |
| `p.joinpath('fichier.txt')`                 | Concatène des chemins                      |
| `p.parts`                                   | Retourne les composants du chemin          |
| `p.suffix` / `p.stem` / `p.name`            | Extension, nom sans extension, nom complet |

---

## 🧭 Module `sys` — Accès bas-niveau à l’interpréteur

| Attribut / Fonction                       | Description                             |
| ----------------------------------------- | --------------------------------------- |
| `sys.argv`                                | Liste des arguments du script           |
| `sys.exit([code])`                        | Quitte le programme                     |
| `sys.path`                                | Chemins de recherche des modules        |
| `sys.platform`                            | Plateforme (`'win32'`, `'linux'`, etc.) |
| `sys.version`                             | Version complète de Python              |
| `sys.stdout` / `sys.stderr` / `sys.stdin` | Flux standard                           |
| `sys.getsizeof(obj)`                      | Taille mémoire d’un objet               |
| `sys.modules`                             | Modules actuellement chargés            |

---

## 🕓 Module `datetime` — Dates et heures

| Classe / Méthode                               | Description                    |
| ---------------------------------------------- | ------------------------------ |
| `datetime.date.today()`                        | Date du jour                   |
| `datetime.datetime.now()`                      | Date et heure actuelles        |
| `datetime.datetime.strptime(date_str, format)` | Convertit une chaîne en date   |
| `datetime.datetime.strftime(format)`           | Formate une date en texte      |
| `datetime.timedelta(days=1)`                   | Durée (ajouts / soustractions) |
| `datetime.datetime.utcnow()`                   | Heure UTC actuelle             |
| `datetime.datetime.timestamp()`                | Convertit en timestamp         |
| `datetime.datetime.fromtimestamp(ts)`          | Convertit un timestamp         |

---

## 📦 Module `shutil` — Fichiers et répertoires

| Fonction                                        | Description                           |
| ----------------------------------------------- | ------------------------------------- |
| `shutil.copy(src, dst)`                         | Copie un fichier                      |
| `shutil.copytree(src, dst, dirs_exist_ok=True)` | Copie récursive                       |
| `shutil.move(src, dst)`                         | Déplace un fichier/dossier            |
| `shutil.rmtree(path)`                           | Supprime un dossier récursivement     |
| `shutil.disk_usage(path)`                       | Espace disque total / utilisé / libre |
| `shutil.which(program)`                         | Trouve le chemin d’un exécutable      |

---

## 🧨 Module `subprocess` — Exécution de commandes externes

| Fonction                                              | Description                       |
| ----------------------------------------------------- | --------------------------------- |
| `subprocess.run(cmd, capture_output=True, text=True)` | Exécute une commande              |
| `subprocess.Popen([...])`                             | Lance un processus avancé         |
| `subprocess.call([...])`                              | Exécute une commande simple       |
| `subprocess.check_output([...])`                      | Retourne la sortie d’une commande |
| `subprocess.DEVNULL`                                  | Redirige la sortie vers le néant  |

---

## 🧠 Module `platform` — Infos système

| Fonction                    | Description      |
| --------------------------- | ---------------- |
| `platform.system()`         | Nom de l’OS      |
| `platform.release()`        | Version de l’OS  |
| `platform.version()`        | Détails système  |
| `platform.machine()`        | Architecture CPU |
| `platform.node()`           | Nom du PC        |
| `platform.python_version()` | Version Python   |

---

## 🔍 Module `re` — Expressions régulières

| Fonction                           | Description                      |
| ---------------------------------- | -------------------------------- |
| `re.match(pattern, string)`        | Correspondance au début          |
| `re.search(pattern, string)`       | Recherche dans le texte          |
| `re.findall(pattern, string)`      | Liste toutes les correspondances |
| `re.finditer(pattern, string)`     | Itérateur de correspondances     |
| `re.sub(pattern, repl, string)`    | Remplace les occurrences         |
| `re.split(pattern, string)`        | Coupe selon un motif             |
| `re.compile(pattern)`              | Précompile une regex             |
| `match.group()` / `match.groups()` | Résultats de correspondance      |

---

## 🧾 Module `json` — Sérialisation JSON

| Fonction                         | Description                                  |
| -------------------------------- | -------------------------------------------- |
| `json.load(file)`                | Lit du JSON depuis un fichier                |
| `json.loads(str)`                | Convertit une chaîne JSON → objet Python     |
| `json.dump(obj, file, indent=4)` | Écrit un objet Python → JSON dans un fichier |
| `json.dumps(obj, indent=4)`      | Convertit un objet Python → chaîne JSON      |

---

## 💾 Module `pickle` — Sérialisation binaire

| Fonction                                   | Description              |
| ------------------------------------------ | ------------------------ |
| `pickle.dump(obj, file)`                   | Sérialise un objet       |
| `pickle.load(file)`                        | Désérialise un objet     |
| `pickle.dumps(obj)` / `pickle.loads(data)` | Sérialisation en mémoire |

---

## 🌐 Module `socket` — Réseaux

| Fonction                           | Description                 |
| ---------------------------------- | --------------------------- |
| `socket.socket()`                  | Crée un socket              |
| `s.bind((host, port))`             | Attache à une adresse       |
| `s.listen([backlog])`              | Écoute les connexions       |
| `s.accept()`                       | Accepte un client           |
| `s.connect((host, port))`          | Se connecte à un serveur    |
| `s.send(data)` / `s.recv(bufsize)` | Envoie / reçoit des données |
| `s.close()`                        | Ferme le socket             |

---

## 🧩 Module `argparse` — Paramètres de ligne de commande

| Élément                                       | Description         |
| --------------------------------------------- | ------------------- |
| `parser = argparse.ArgumentParser()`          | Crée un parseur     |
| `parser.add_argument('--option', help='...')` | Définit un argument |
| `args = parser.parse_args()`                  | Lit les arguments   |
| `args.option`                                 | Accès à la valeur   |

---

## 🔢 Module `math` — Fonctions mathématiques

| Fonction                                 | Description                   |
| ---------------------------------------- | ----------------------------- |
| `math.pi`, `math.e`                      | Constantes                    |
| `math.sqrt(x)`                           | Racine carrée                 |
| `math.pow(x, y)`                         | Puissance                     |
| `math.floor(x)` / `math.ceil(x)`         | Arrondi inférieur / supérieur |
| `math.sin()`, `math.cos()`, `math.tan()` | Fonctions trigonométriques    |
| `math.log(x, base)`                      | Logarithme                    |
| `math.factorial(x)`                      | Factorielle                   |
