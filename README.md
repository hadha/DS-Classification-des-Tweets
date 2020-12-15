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
- _Classer les tweets : regrouper ensemble les tweets qui sont similaires. C’est une étape qui peut être considérée comme une étape._

## Installation
_1 - <b>La bibliothéque tweepy</b>: Tweepy prend en charge l'accès à Twitter via l'authentification de base et la nouvelle méthode, OAuth. Twitter a cessé d'accepter l'authentification de base, donc OAuth est désormais le seul moyen d'utiliser l'API Twitter._<br/>
Tweepy donne accès à l'API Twitter bien documentée. Avec tweepy, il est possible d'obtenir n'importe quel objet et d'utiliser n'importe quelle méthode proposée par l'API Twitter officielle.<br/>
``pip install tweepy``
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

## I - Prétraitement des données

## II - NLTK
#### Les étapes nécessaires comprennent
Tokenizing sentences pour décomposer le texte en phrases, mots ou autres unités<br/>
Removing stop words like “if,” “but,” “or,” and so on<br/>
Normalizing words en condensant toutes les formes d'un mot en une seule forme<br/>
Vectorizing text en transformant le texte en représentation numérique pour la consommation de nos classificateur

 - <b>Tokenizing</b>
<br/>
La tokenisation est le processus de décomposition de morceaux de texte en plus petits morceaux. spaCy est livré avec un pipeline de traitement par défaut qui commence par la tokenisation, ce qui rend ce processus un jeu d'enfant. Dans spaCy, vous pouvez effectuer soit une tokenisation de phrase, soit une tokenisation de mot:<br/>
Word tokenization décompose le texte en mots individuels.<br/>
Sentence tokenization décompose le texte en phrases individuelles.<br/>
<br/>
- <b>Removing Stop Words</b>
<br/>
Stop Words sont des mots qui peuvent être importants dans la communication humaine mais qui ont peu de valeur pour les machines. spaCy est livré avec une liste par défaut de mots vides que vous pouvez personnaliser<br/>
<br/>
- <b>Normalizing Words</b>
<br/>
La normalisation est un peu plus complexe que la tokenisation. Cela implique de condenser toutes les formes d'un mot en une seule représentation de ce mot.
<br/>
- Stemming
- Lemmatization
<br/>
<b>Stemming</b> : un mot est coupé à sa racine, la plus petite unité de ce mot à partir de laquelle vous pouvez créer les mots descendants. Vous venez de voir un exemple de cela ci-dessus avec "montre". La racine tronque simplement la chaîne en utilisant des terminaisons communes, de sorte qu'elle manquera la relation entre «sentir» et «ressenti», par exemple.
<br/>
<b>Lemmatization</b> : cherche à résoudre ce problème. Ce processus utilise une structure de données qui relie toutes les formes d'un mot à sa forme la plus simple, ou lemme. Parce que la lemmatisation est généralement plus puissante que la tige, c'est la seule stratégie de normalisation proposée par spaCy.
<br/>
<br/>
- <b>Vectorizing Text</b>
<br/>
est un processus qui transforme un jeton en un vecteur, ou un tableau numérique qui, dans le contexte de la NLP, est unique et représente diverses caractéristiques d'un jeton. Les vecteurs sont utilisés sous le capot pour trouver des similitudes de mots, classer le texte et effectuer d'autres opérations NLP.



