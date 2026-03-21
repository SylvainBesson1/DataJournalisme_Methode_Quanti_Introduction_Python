**Installation** écrite par **Alioscha Massein** Ingénieur d'étude en statistique
*Maison des Sciences sociales et des Humanités (MSH) Lyon - Saint Etienne*  
aljoscha.massein@msh-lse.fr

# Préambule

## Installation de Python

Mais avant, qu'est-ce que c'est que Python ? Python est un langage de programmation, c'est-à-dire un langage qui permet de créer des logiciels, des applications, des sites web, etc. c'est-à-dire un langage un peu compliqué mais accessible pour faire réaliser des tâches à votre ordinateur. 

Utiliser un langage de programmation permet tout d'abord de pouvoir réaliser des actions qu'une application tierce ne pourrait pas réaliser, ou bien de créer des applications sur mesure en fonction des tâches que vous souhaitez réaliser. De plus, Python est un des langages de programmation les plus polyvalents et avec une des communautés les plus importantes. Et puisque l'on s'intéresse aux données, ça tombe bien, c'est également un des langages de programmation qui est le plus utilisé pour la *data science*. De nombreux développeurs, entreprises, activistes et journalistes utilisent, développent et mettent à disposition des outils écrits en Python.

Pour installer Python, nous allons commencer par installer une application que l'on appelle un ***gestionnaire de package***.

Un gestionnaire de package est une application qui permet d'installer, mettre à jour et supprimer des applications qui sont utilisés par votre ordinateur. En pratique, on peut s'en servir pour gérer l'ensemble des applications qui sont installés sur notre ordinateur, mais on s'en sert surtout pour installer de petits utilitaires qui n'ont pas forcément *d'interface graphique*, on parle aussi d'outils en *CLI (command-line interface)*, c'est-à-dire une **interface en ligne de commande**. 

Ici, nous n'allons utiliser qu'un gestionnaire de package pour Python, c'est-à-dire un utilitaire qui permet de créer des projets en Python, gérer les versions de Python, et les **librairies** que vous allez utiliser en plus de python (appellées aussi bibliothèques, modules, ou encore... packages, ce sont des outils développés par d'autres personnes que l'on peut réutiliser). Ces derniers temps, un gestionnaire de package Python est de plus en plus utilisé : il s'agit d'un petit outil qui s'appelle [`uv`](https://docs.astral.sh/uv/). `uv` a plusieurs avantages : 
- Il regroupe l'ensemble des autres gestionnaires de paquet Python en une seule interface
- Il est très, très rapide
- Il est assez fort pour gérer les conflits de dépendances (certaines versions de librairies peuvent être incompatibles ensembles).


En fonction de votre **système d'exploitation** (MacOs, Linux, Windows, iOS, Android...), nous n'allons pas installer `uv` de la même manière. Dans tous les cas, vous n'allez pas échapper à votre ***terminal***. 

## Sur Windows
Si vous êtes sur Windows, vous allez avoir besoin d'ouvrir un outil qui s'appelle **powershell**, que vous trouverez en cherchant dans les applications installées sur votre ordinateur. Powershell est une application qui simule un terminal, et qui execute son propre langage de script (le powershell), qui partage des commandes avec un **shell** classique (bash, zsh, etc.), mais qui embarque aussi ses propres commandes. Pour installer `uv` sur Windows, vous allez taper ou copier dans votre **powershell** :
````bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
````

En utilisant cette commande, cela devrait installer le gestionnaire de package `uv` sur votre ordinateur. Vous pouvez ensuite l'utiliser sur powershell, ou n'importe quel autre outil de type terminal. On peut vérifier que l'installation s'est déroulée sans problème en testant cette commande :
````bash
uv --version
````
Le résultat devrait être le numéro de version de `uv` que vous avez installé, sous la forme :
> uv 0.XX.YY (SOMETHING DATE)

## Linux ou MacOS

Sur Linux ou MacOs, vous pouvez utiliser l'application **terminal** pour ouvrir votre interface en ligne de commande. Sur ces deux système d'exploitation UNIX, vous utilisez un langage qui s'appelle **shell** (bash, zsh, etc.) pour interagir avec votre ordinateur (et le terminal). Pour installer `uv`, vous pouvez utiliser la commande suivante : 
````bash
curl -LsSf https://astral.sh/uv/install.sh | sh
### If you don't have curl install on your computer
wget -qO- https://astral.sh/uv/install.sh | sh
````

Si tout a bien été installé, vous devriez pouvoir lancer la commande suivante : 

````bash
uv --version
````


## Installation de Python

Pour installer, gérer, mettre à jour et supprimer Python, vous pouvez utiliser `uv` très simplement. Dans un terminal (ou un powershell), écrivez cette commande : 
````bash
uv python3.12 install
````
En utilisant cette commande, vous installez la version 3.12 de Python, celle que nous allons utiliser ici. Mais vous pourriez installer une autre version si vous le souhaitez. Vous pouvez voir l'ensemble des versions disponibles (et les versions que vous avez installé) à l'aide de la commande suivante : 
````bash
uv python list
````

Par défaut, il existe une version de Python installé sur la plupart des ordinateurs qui utilisent MacOS.



## Installation d'un environnement de développement intégré (IDE)

Sous ce nom un peu compliqué se cache les applications qui permettent de faire de l'édition de code informatique. En pratique le code informatique peut tout à fait s'écrire sur un éditeur de texte classique, comme TextEdit, NotePad++... mais ces logiciels ne proposent pas un environnement complet de programmation qui facilite l'écriture, la gestion, le partage et l'exécution de code informatique. 

Dans le cadre de ce cours, nous avons fait le choix de vous faire utiliser l'application [**Visual Studio Code**](https://code.visualstudio.com/), qui est un IDE très utilisé. Sachez néanmoins que VSCode (son petit nom) n'est pas un logiciel libre ou Open source, mais un outil développé et commercialisé par Microsoft. Il existe de nombreuses alternatives à VSCode, comme VSCodium (version *open source* de VScode), Positron, Spyder, Vim (pour les utilisateurs avancés), Emacs,  Atom, etc. Vous êtes libre de travailler avec les outils qui vous correspondent le mieux en terme d'interface ou d'éthique. 

Néanmoins, nous vous proposerons ce cours sur l'interface de VSCode, car c'est un outil très utilisé et qui a des mises à jour régulières.

## Déploiement d'un premier projet Python

Une fois, *uv*, *Python* et *VSCode* installés, vous pouvez créer votre premier projet Python de la manière suivante. 
En premier cliquez sur **Fichier** > **Ouvrir un dossier** et créez un dossier dans lequel vous allez stocker votre projet, ou plutôt ici votre cours. Appelez-le comme vous le souhaitez, nous l'appelerons **coursM1_datajournaliste_python**. 

Le dossier créé, vous allez pouvoir ouvrir un terminal en cliquant sur **Terminal** > **Nouveau terminal**. Dans le terminal, nous allons créer un nouveau projet avec *uv*. 

## Déploiement des librairies depuis un fichier uv.lock ou d'un fichier requirements.txt

Dans certains cas, vous êtes amené à partager et réutiliser du code. Dans la grande majorité des cas, vous utiliserez un petit outil qui s'appelle **git**. **Git** est un outil de gestion de version, ce qui signifie que vous pouvez enregistrer les évolutions d'un fichier dans le temps : fini les V1, V2, V3_Final_presquefini... le second avantage de git, c'est le lien qui est fait avec des *forges logicelles* dont les plus connues sont **GitHub** et **GitLab**. On peut se servir de ces plateformes pour hébeger du code, et de manière générale, pour collaborer à distance.

Dans notre cas, nous allons télécharger le code sans nous servir de **git** car il faudrait installer l'utilitaire sur votre ordinateur. Libre à vous de le faire si vous le souhaitez, mais nous n'aborderons pas ce point ici. Vous pouvez télécharger le dossier du cours au format .zip, et décompresser l'archive zip. Une fois l'archive décompressé, nous allons l'ouvrir avec VSCode afin d'être dans l'environnement du dossier. 

Une fois dans le dossier, nous allons créer **l'environnement virtuel** qui permet d'utiliser toutes les librairies du cours, c'est-à-dire l'ensemble des ressources externes que nous allons devoir utiliser en plus de Python. Pour cela, nous pouvons utiliser deux méthodes : soit il existe un fichier **uv.lock** qui précise les librairies à installer avec `uv`, soit il existe un fichier requirements.txt qui permet d'installer les librairies avec un utilitaire qui s'appelle `pip` qui est installé avec Python et avec `uv`. 
#### Si vous avez un fichier uv.lock
Dans ce cas, c'est très simple. Il vous faut ouvrir un terminal, vérifier que vous êtes bien dans le dossier, et vous pouvez lancer la commande :
````bash
uv sync
````
En executant cette commande, `uv` créé pour vous un environnement virtuel dans un dossier `.venv`, et installe toutes les librairies dont vous aurez besoin pour ce cours. 

#### Si vous avez un fichier requirements.txt
Dans ce cas, il vous faudra dans un premier temps créer l'environnement virtuel en amont :
````bash
uv venv #Pour créer l'environnement virtuel
# Pour activer l'environnement
source .venv/bin/activate # sur macOS et Linux
.\venv\Scripts\activate # sur Windows.

uv pip install -r requirements.txt #Pour installer les librairies
````

Une fois que vos librairies sont installées, vous pouvez utiliser l'environnement virtuel pour suivre le cours. 

### Encore quelques tips avec uv

`uv` permet donc de gérer les librairies dans un projet python, et de faire pas mal d'autre choses. Voici les principales commandes que nous allons utiliser : 

#### Installer et désinstaller des librairies

Vous pouvez gérer les dépendances de votre projet avec deux commandes : 
````bash
uv add lalibrairiedevosreves
uv remove lalibrairienulle
````

Vous pouvez voir l'ensemble des commandes disponibles avec `uv` ici : 
````bash
uv -h
#ou
uv --help
````