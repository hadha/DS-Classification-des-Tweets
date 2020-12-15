# Classification des Tweets

_**Hadhémi Gharbi**_<br/>
_**3 DNI Groupe 1**_

## Description du projet

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

_3 - _


