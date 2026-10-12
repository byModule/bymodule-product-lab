# 001 : Le contenu des formations vit dans des fichiers structurés et se vérifie comme du code

*English version: [001-content-as-tested-structured-files.md](001-content-as-tested-structured-files.md)*

- **Date :** 2026-09-28 (compilateur et lint introduits ; règle anti-fuite ajoutée le 2026-09-30 ; rédigée en octobre 2026)
- **Statut :** Adoptée
- **Domaine :** contenu · plateforme

## Contexte

Fin septembre 2026, le catalogue comptait 31 formations, chacune en français et en anglais. Toutes suivent le même standard de contenu : objectifs pédagogiques, notions, prérequis, idées reçues fréquentes, sources avec date de vérification, évaluations, et une structure de leçon fixe qui se termine par une mise en pratique et une vérification de compréhension.

Jusque-là, les premières formations étaient écrites sous forme de données dans le code de l'application. Cela fonctionnait pour quelques formations, mais rien ne vérifiait automatiquement le standard. Une leçon sans objectif pédagogique, un quiz dont la réponse se devinait, ou une leçon française sans son équivalent anglais n'apparaissaient qu'à la relecture. Avec 31 formations bilingues et une seule personne pour les relire, la relecture n'est pas un contrôle fiable.

Une deuxième contrainte venait des moteurs de recherche. Les pages publiques ont besoin d'un texte descriptif sur chaque leçon, alors que le contenu de la leçon lui-même est payant. Sans vérification, une description publique peut facilement reprendre mot pour mot du contenu payant.

## Options

| Option | Pour | Contre |
| --- | --- | --- |
| A. Garder les formations sous forme de données dans l'application | Aucun nouvel outil ; fonctionne déjà | Aucune vérification automatique du standard ; modifications de contenu et de code mêlées dans les mêmes fichiers ; difficile de relire une formation à part |
| B. Un CMS headless | Interface d'édition confortable ; une API | Un service de plus à faire tourner et à payer ; le standard serait toujours vérifié à la main ; la parité entre français et anglais n'est pas garantie |
| C. Des fichiers sources structurés par formation, compilés et passés au lint avant la mise en ligne | Le standard est vérifié à chaque modification ; historique complet ; français et anglais côte à côte ; une formation se relit comme n'importe quelle autre modification | Pas d'éditeur visuel ; le compilateur et le lint doivent être écrits et maintenus |

## Décision

Option C. Le critère qui a tranché : **un standard qui n'est pas vérifié automatiquement ne tiendra pas sur 31 formations bilingues maintenues par une seule personne.**

Le fonctionnement, dans son principe :

- **Un ensemble de fichiers structurés par formation et par langue** : le texte des leçons avec un petit nombre de blocs typés (exemple, idée reçue, points clés, mise en pratique, vérification), plus les métadonnées de la formation.
- **Un compilateur transforme ces fichiers en trois sorties**, chacune pour un usage différent :
  - un **programme public** pour le catalogue, les pages de formation et les moteurs de recherche (métadonnées, plan, objectifs) ;
  - le **contenu de lecture** servi aux apprenants qui y ont accès (contenu des leçons, exercices, questions d'auto-évaluation) ;
  - une **couche de connaissances** conservée côté serveur pour des travaux futurs (faits typés, notions, évaluations). C'est une fondation, pas un système de recherche documentaire déployé.
- **Un lint s'exécute à chaque modification et bloque la mise en ligne en cas d'erreur** : structure invalide, identifiants en double, versions française et anglaise désynchronisées (mêmes modules, leçons et slides, dans le même ordre), liens cassés entre objectifs, notions, idées reçues et évaluations. Il signale aussi les écarts au standard : une leçon sans objectif pédagogique, un objectif de formation qu'aucune leçon ne couvre, une notion utilisée avant d'être introduite, un contenu qui évolue vite sans date de vérification. Des contrôles qualité distincts rejettent les quiz dont la répartition des réponses trahit la bonne option.
- **Une règle anti-fuite** empêche les champs publics destinés aux moteurs de recherche de reprendre du contenu payant : une description ou une question publique qui partage une séquence de mots assez longue avec le contenu de la leçon fait échouer le lint et doit être reformulée.

Avant de basculer, j'ai figé le rendu des formations existantes et vérifié que le nouveau format le reproduisait, pour que la migration ne modifie pas en silence ce que voyaient les apprenants. Les formations existantes ont été migrées le 28 septembre 2026, et les formations du programme 2026 ont été intégrées dans le même format le lendemain.

## Conséquences

- **Ce que cela rend possible :** chaque nouvelle formation passe par les mêmes vérifications que les formations existantes, et les pages publiques peuvent porter davantage de texte descriptif sans exposer le contenu payant. En octobre 2026, un test a été ajouté pour vérifier que chaque formation est intégrée de la même manière (recommandation de l'onboarding, certificats, paiement, visibilité dans le catalogue).
- **Ce que cela coûte :** il n'y a pas d'éditeur visuel. Changer une virgule passe par une modification relue, ce qui est acceptable pour un seul auteur et serait à revoir si d'autres auteurs arrivent.
- **Ce que cela ne garantit pas :** la qualité pédagogique. Le lint vérifie la structure, pas la clarté d'une explication ni la pertinence d'un exemple ; cela reste relu par une personne.
- **À surveiller :** le nombre d'erreurs que le lint détecte avant la mise en ligne, comparé aux erreurs signalées par les apprenants après, et le délai entre un sujet de formation et une formation publiée, relecture comprise. Je regarderai les deux après les formations prévues pour janvier 2027.

## Revue

*Pas encore revue. Prévue après la publication des formations de janvier 2027.*
