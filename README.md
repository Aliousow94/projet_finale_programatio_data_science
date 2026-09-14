\# Rapport de Projet Final - Programmation Data Science 

\*\*Université Amadou Mahtar Mbow (UAM)\*\*  

\*UFR STA / Département MIM — Licence 3 Informatique\*  



\## Auteur

\* \*\*Mamadou Aliou SOW\*\* — Étudiant en L3 Informatique



\## Encadrants

\* \*\*Pr Amadou Dahirou GUEYE\*\*

\* \*\*Mrs Papa Assane DIOP\*\*



\---



\## Présentation \& Objectifs du Projet

Ce projet a pour but d'analyser les facteurs académiques, démographiques et comportementaux qui influencent la \*\*réussite ou l'échec scolaire\*\* d'une population de \*\*1000 étudiants\*\*. 



L'objectif principal est de concevoir un système automatisé capable d'identifer de manière précoce les profils d'étudiants en situation de décrochage afin de permettre à l'administration de l'UAM de mettre en place des mesures d'aide ciblées.



\### Principales étapes du cycle de vie du projet :

1\. \*\*Nettoyage \& Préparation :\*\* Traitement des 29% de données manquantes sur les heures d'étude et notes de CC (imputation par la médiane) et suppression des doublons via Pandas.

2\. \*\*Encodage :\*\* Conversion des données qualitatives via `LabelEncoder` et `OneHotEncoder` pour préparer les algorithmes.

3\. \*\*Analyse Exploratoire \& Visualisation :\*\* Analyse des distributions et intercorrélations à l'aide de `Matplotlib` et `Seaborn`.

4\. \*\*Modélisation :\*\* Entraînement d'un algorithme d'Arbre de Décision (`DecisionTreeClassifier`).



\---



\## Faits Saillants de l'Analyse Exploratoire

\* \*\*Performances Globales :\*\* La moyenne générale s'établit à \*\*14/20\*\*, révélant néanmoins une forte hétérogénéité avec des notes s'étalant de 6,62 à 20,00/20.

\* \*\*Impact du Travail Personnel :\*\* Le Scatter plot montre une trajectoire linéaire positive très marquée entre les heures d'étude hebdomadaires et la moyenne générale.

\* \*\*Impact de l'Absentéisme :\*\* À l'inverse, l'accumulation des absences engendre une dégradation brutale de la moyenne.

\* \*\*Filières \& Sexe :\*\* L'analyse graphique prouve l'absence d'un "effet filière" ou d'un facteur lié au genre sur la note finale, les résultats étant très homogènes.



\---



\## Conclusion Critique : Le Piège du Data Leakage

Bien que le modèle d'Arbre de Décision affiche des métriques parfaites (\*\*Accuracy, Précision et Rappel à 100 %\*\*), l'analyse critique a révélé une \*\*fuite de données (Data Leakage)\*\* majeure :

\* Le modèle a conservé les variables de performance directe (`moyenne`, `note\_examen`, `note\_cc`).

\* L'arbre n'a donc pas appris à anticiper, mais s'est borné à redécouvrir la règle arithmétique de l'université (Moyenne < 10 = Échec).



\### Recommandations pour l'Évolution du Projet

Pour rendre le modèle pleinement opérationnel et utile dès le début d'un semestre pour l'UAM, il est recommandé de :

1\. \*\*Retirer immédiatement\*\* les variables liées aux notes finales.

2\. \*\*Réentraîner le modèle\*\* en se basant uniquement sur les données comportementales disponibles précocement (`absences`, `heures\_etude`, `participation\_td`).



