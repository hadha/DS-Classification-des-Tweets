[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/hadha/DS-Classification-des-Tweets/main)

# Classification des Tweets

_**Hadhémi Gharbi**_<br/>
_**3 DNI Groupe 1**_

[![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)
[![forthebadge](https://forthebadge.com/images/badges/made-with-markdown.svg)](https://forthebadge.com)


## Description du projet
Twitter est une mine d'or de données. Contrairement aux autres plates-formes sociales, presque tous les tweets des utilisateurs sont entièrement publics et extractibles. C'est un énorme avantage si vous essayez d'obtenir une grande quantité de données sur lesquelles exécuter des analyses. Les données Twitter sont également assez spécifiques. L'API de Twitter nous permet d'effectuer des requêtes complexes, comme extraire chaque tweet sur un certain sujet au cours des vingt dernières minutes, ou extraire les tweets non retweetés d'un certain utilisateur.<br/>
Donc dans le projet nous allons extraire les tweets avec notre API pour analyser les mots avec la bibliothèque NLTK puis nous les regrouperons selon leur thème que nous avons choisi avec KMEANS

## Objectifs du projet
- _Maitriser l’API de twitter pour l’extraction des tweets<br/>_
- _Maitriser la partie NLP (natural language processing) avec NLTK en Python<br/>_
- _Appliquer les principes de nettoyage des données<br/>_
- _Classer les tweets : regrouper ensemble les tweets qui sont similaires._

## Plan du projet
### I - Importation des bibliothéques<br/>
### II - Accéder à l'API Twitter<br/>
### III - Extraction des tweets<br/>
### IV - Fusionner les fichiers CSV<br/>
### V - Data Preparation<br/>
#### 1 - Chargement des données : Data Retrievel<br/>
#### 2 - Les informations statistiques sur les données<br/>
#### 3 - Les missings values<br/>
#### 4 - Les types des donneés : Numériques ou Catégoriques<br/>
#### 5 - Visualisation des histogrammes des variables numériques<br/>
#### 6 - La corrélation entre les variables<br/>
### VI -Prétraitement des tweets : Cleaning Data<br/>
#### 1 - Supprimer les noms des utilisateurs<br/>
#### 2 - Remplacer une expression<br/>
### VII - NLTK<br/>
#### 1 - Tokenization<br/>
#### 2 - Stopwords & emotions & Punctiations<br/>
#### 3 - Normalizing Words<br/>
#### 4 - Vectorization<br/>
### VIII - Clustering : KMeans<br/>
### IX - Analyse des Sentiments<br/>
### X - Analyse des sources<br/>
### XI - Conclusion<br/>

<hr>

## I - Importation des bibliothéques
_1 - <b>La bibliothéque tweepy</b>: Tweepy prend en charge l'accès à Twitter via l'authentification de base et la nouvelle méthode, OAuth. Twitter a cessé d'accepter l'authentification de base, donc OAuth est désormais le seul moyen d'utiliser l'API Twitter._<br/>
Tweepy donne accès à l'API Twitter bien documentée. Avec tweepy, il est possible d'obtenir n'importe quel objet et d'utiliser n'importe quelle méthode proposée par l'API Twitter officielle.<br/>
``pip install tweepy``
<br/>
<br/>
_2 - <b>La bibliothéque nltk</b>: Natural Language Toolkit (NLTK) est une boîte-à-outil permettant la création de programmes pour l'analyse de texte._<br/>
``pip install nltk``<br/><br/>
_La première chose à faire pour utiliser NLTK est de télécharger ce qui se nomme le NLTK corpora._<br/>
``import nltk``<br/>
``nltk.download()``<br/>
<br/>
_Un corpus est défini de cette façon :_
<br/>
Corpus, pluriel , corpora ; Une collection de données linguistiques, parfois une compilation de textes écrits, ou de transcriptions d'enregistrement de discours. La raison principale d'un corpus est de vérifier une hypothèse sur le langage - par exemple : déterminer comment l'utilisation d'un son particulier, d'un mot ou d'une construction syntaxique varie. Les corpus linguistiques agissent avec les lois et les pratiques d'utilisation de corpora dans l'étude du langage. Un corpus informatique contient un ensemble vaste de textes traduisibles en langage-machine.
<br/>
Ainsi, un corpus est tout simplement un énorme ensemble de textes.
<br/>
<br/>
<b>"Stop Words"</b>
Parfois, nous avons besoin de "raboter" des éléments inutiles afin que les données soient davatange traduisibles pour l'ordinateur. En NLP, de telles données (des mots, words) sont qualifiées par stop words. Par conséquent, ces mots n'ont aucune signification pour nous, et nous souhaiterions les retirer.
<br/>
La libraire NLTK contient quelques mots "d'arrêt" pour commencer ce traitement. Pour les connaître, écrivons ce petit script :<br/>
``from nltk.corpus import stopwords``<br/>
Nous avons ainsi listé une collection non-ordonnée d'éléments, connu comme "mots d'arrêt", en langue anglaise, dans ce cas.
<br/>
``from nltk.tokenize import word_tokenize``<br/>
_La "tokénisation", telle qu'il s'agit du processus consistant à briser un flux de texte en plusieurs mots, phrases, symboles ou tout autre élements significatifs dénommés Signes (tokens)._<br/>
la fonction ``word_tokenize()`` découpe de chaîne de signes selon la ponctuation, en dehors des points.

_ 3 - **La bibiliothéque Twython** est une bibliothèque Python offrant un moyen facile d'accéder aux données Twitter. _<br/>
``pip install twypthon``<br/>
<br/>

_ 4 - **TextBlob** est une bibliothèque Python pour le traitement de données textuelles. Il fournit une API simple pour plonger dans les tâches courantes de traitement du langage naturel (PNL) telles que le marquage d'une partie du discours, l'extraction de phrases nominales, l'analyse des sentiments, la classification, la traduction, etc. _<br/>
``pip install textblob``<br/>
<br/>

5 - **Le module re** fournit des modèles d'expressions régulières de style Perl. Les expressions régulières en Python nécessitent d'importer le module natif re.<br/>
``pip install regex``<br/>
<br/>

## II - Accéder à l'API Twitter
<p align="center">
  <img src="https://github.com/hadha/DS-Classification-des-Tweets/blob/main/Gif/img.PNG" width="350">
 </p>
 
 <hr>

## III - Extraction des tweets
Nous avons choisi 5 thèmes différents :<br/>
1- Marketing<br/>
2- Travel<br/>
3- Google<br/>
4- Huawei<br/>
5- Cars<br/>
6- Cristiano Ronaldo<br/>

Et pour chaque théme nous avons crée un fichier csv
<br/>
![](Gif/extraction.gif)
<hr>

## IV - Fusionner les fichiers CSV
Dans cette étape, nous avons regroupé tous les thèmes dans un seul fichier csv
<br/>
![](Gif/fusionner.gif)
<hr>

## V - Data Preparation
Le terme « préparation des données » désigne les opérations de nettoyage et transformation qui doivent être appliqués aux données brutes avant leur traitement et analyse. Il s’agit d’une étape importante avant le traitement proprement dit, qui implique souvent de reformater et corriger les données et de combiner des datasets pour enrichir certaines données.
La première étape de la data preparation consiste à pouvoir accéder aux données de n’importe quelle source, quel qu’en soit l’origine, le récit ou le format.
<br/>
<br/>

### 1 - Chargement des données : Data Retrievel
Avec la commande ``pd.read_csv`` nous pouvons lire nos données.

<hr>

### 2 - Les informations statistiques sur les données
Avec la commande ``.describe()`` nous pouvons faire des statistiques sur nos données

<hr>

### 3 - Les missings values
Pour voir les valeurs manquantes qu'on a.

<hr>

### 4 - Les types des donneés : Numériques ou Catégoriques
Connaître les types de nos données.
<br/>
Les données numériques concernent des données représentées sous un format compatible avec un ordinateur. Un ordinateur ne peut traiter que des données numériques, puisqu'il fonctionne en mode binaire.
<br/>
Une variable catégorique est une variable où chaque réponse peut être classée dans une catégorie particulière.
<br/>

<hr>

### 5 - Visualisation des histogrammes des variables numériques
Le but de la visualisation de données étant de représenter graphiquement des données brutes

<hr>

### 6 - La corrélation entre les variables
Une corrélation est une relation qu’il y a entre différentes variables<br/>
<br/>
![](Gif/corr.gif)
<hr>

## VI -Prétraitement des tweets : Cleaning Data
### 1 - Supprimer les noms des utilisateurs
Un nom précédé d'arobase « @ » est un lien vers le compte Twitter de l'utilisateur de ce nom (qui permet de voir tous ses tweets, sauf s'ils sont protégés)<br/>
Le module de string de Python fournit des constantes pour les opérations liées aux chaînes.<br/>
Le module re a été spécialement conçu pour travailler avec les expressions régulières (Regular Expressions). Il définit plusieurs fonctions utiles, que nous allons découvrir, ainsi que des objets propres pour modéliser des expressions.<br/>
![](Gif/user.gif)

### 2 - Remplacer une expression
Un mot précédé du signe « # » (croisillon) est un hashtag. Il s'agit d'un sujet attribué au message, Twitter peut afficher tous les tweets comportant un hashtag précis, et établit un classement des mots ou bien des hashtags du moment les plus utilisés.<br/>
D'abord, on trouve un caractère accent circonflexe ^ qui veut dire qu'on cherche l'expression au début de la chaîne. Vous pouvez aussi voir, à la fin de la regex, le symbole $ qui veut dire que l'expression doit être à la fin de la chaîne. Si l'expression doit être au début et à la fin de la chaîne, cela signifie que la chaîne dans laquelle on recherche ne doit rien contenir d'autre que l'expression.<br/>
Nous avons ensuite une classe de caractère [0-9]. Cela signifie qu'après le 0, on doit trouver un chiffre compris entre 0 et 9 (peut-être 0, peut-être 1, peut-être 2…).
<br/>
Pour remplacer une partie d'une chaîne de caractères sur la base d'une regex, nous allons utiliser la fonction sub du module re.<br/>
Elle prend trois paramètres :<br/>
l'expression à rechercher ;<br/>
par quoi remplacer cette expression ;<br/>
la chaîne d'origine.
<br/>

<hr>

## VII - NLTK

#### Les étapes nécessaires comprennent
1 - Tokenizing sentences pour décomposer le texte en phrases, mots ou autres unités<br/>
2 - Removing stop words like “if,” “but,” “or,” and so on<br/>
3 - Normalizing words en condensant toutes les formes d'un mot en une seule forme<br/>
4 - Vectorizing text en transformant le texte en représentation numérique pour la consommation de nos classificateur

 ### 1 - Tokenizing
<br/>La tokenisation est le processus de décomposition de morceaux de texte en plus petits morceaux. spaCy est livré avec un pipeline de traitement par défaut qui commence par la tokenisation, ce qui rend ce processus un jeu d'enfant. Dans spaCy, vous pouvez effectuer soit une tokenisation de phrase, soit une tokenisation de mot:<br/>
Word tokenization décompose le texte en mots individuels.<br/>
Sentence tokenization décompose le texte en phrases individuelles.<br/>
![](Gif/tokenize.gif)

### 2 - Removing Stop Words
<br/>
Stop Words sont des mots qui peuvent être importants dans la communication humaine mais qui ont peu de valeur pour les machines. spaCy est livré avec une liste par défaut de mots vides que vous pouvez personnaliser<br/>

### 3 - Normalizing Words
<br/>
La normalisation est un peu plus complexe que la tokenisation. Cela implique de condenser toutes les formes d'un mot en une seule représentation de ce mot.
<br/>
 - Stemming<br/>
 - Lemmatization
<br/>
<b>Stemming</b> : un mot est coupé à sa racine, la plus petite unité de ce mot à partir de laquelle vous pouvez créer les mots descendants. Vous venez de voir un exemple de cela ci-dessus avec "montre". La racine tronque simplement la chaîne en utilisant des terminaisons communes, de sorte qu'elle manquera la relation entre «sentir» et «ressenti», par exemple.
<br/>
<b>Lemmatization</b> : cherche à résoudre ce problème. Ce processus utilise une structure de données qui relie toutes les formes d'un mot à sa forme la plus simple, ou lemme. Parce que la lemmatisation est généralement plus puissante que la tige, c'est la seule stratégie de normalisation proposée par spaCy.

### 4 - Vectorizing Text
<br/>
est un processus qui transforme un jeton en un vecteur, ou un tableau numérique qui, dans le contexte de la NLP, est unique et représente diverses caractéristiques d'un jeton. Les vecteurs sont utilisés sous le capot pour trouver des similitudes de mots, classer le texte et effectuer d'autres opérations NLP.

<hr>

## VIII - Clustering : KMeans
C’est l’un des algorithmes de clustering les plus répandus. Il permet d’analyser un jeu de données caractérisées par un ensemble de descripteurs, afin de regrouper les données “similaires” en groupes (ou clusters).
![](Gif/kmeans.gif)
<hr>

## IX - Analyse des Sentiments
L’analyse du sentiment (ou de la tonalité), aussi appelé opinion mining, est une notion beaucoup évoquée mais souvent mal comprise.
<br/>
Il s‘agit du processus qui permet de déterminer la tonalité émotionnelle qui se cache derrière une série de mots. Cette analyse est utilisée pour mieux comprendre la perception, les opinions et les émotions exprimées dans une mention en ligne.
![](Gif/sentiments.gif)
<hr>

## X - Analyse des sources
![](Gif/source.gif)
<hr>

## XI - Conclusion
Dans ce projet, nous avons vu l'extraction de tweets et les analyser avec la bibliothèque nltk pour regrouper les thèmes que nous avons choisis.

## Références
[Watermark](https://github.com/rasbt/watermark)
<br/>
[NLTK](https://code.tutsplus.com/fr/tutorials/introducing-the-natural-language-toolkit-nltk--cms-28620)
<br/>
[Analyse des sentiments](https://stackabuse.com/python-for-nlp-sentiment-analysis-with-scikit-learn/)
<br/>
[Cleaning Data](https://www.youtube.com/watch?v=KhXU7KOxQcg&ab_channel=UnfoldDataScience)
<br/>





