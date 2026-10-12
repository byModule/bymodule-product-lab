# Construire Module de 0 à 1

*English version: [01-building-bymodule-from-0-to-1.md](01-building-bymodule-from-0-to-1.md)*

**Auteur :** Alex Dionisio
**Rôle :** fondateur, Product Manager et développeur
**Produit :** [Module](https://bymodule.com)
**Statut :** produit en ligne
**Code source de production :** privé

## Périmètre et éléments de preuve

J'ai construit Module comme une plateforme de formation pour les professionnels qui créent des produits numériques. J'ai conçu l'expérience des apprenants, développé l'application et ses intégrations, et créé le contenu pédagogique dans le cadre de [Module](https://bymodule.io).

Cette étude de cas est mon récit de la première version. Les fonctionnalités livrées et les observations qualitatives ci-dessous sont rapportées par moi. Elles n'ont pas été vérifiées de façon indépendante pour cette publication. Aucun jeu de données d'usage ni aucun résultat business mesuré n'accompagne ce document.

## La première version

Les apprenants devaient pouvoir découvrir une formation, comprendre son programme, créer un compte, accéder au contenu et suivre leur progression. Faire fonctionner le service demandait aussi la facturation, l'administration du contenu, la traduction et la mesure d'audience.

J'ai travaillé sur tous ces sujets au lieu de confier le développement à une équipe d'ingénieurs séparée. Côté produit : la proposition de valeur, les parcours des apprenants, les modèles d'accès et la mesure. Côté développement : le frontend React, les services Firebase, l'intégration Stripe et les interfaces d'administration. Côté contenu : le standard de contenu et la création des 31 formations, en français et en anglais.

## Livré

| Domaine | Fonctionnalités |
| --- | --- |
| Contenu | 31 formations créées en français et en anglais selon un standard de contenu, avec objectifs pédagogiques, prérequis, sources et évaluations. |
| Découverte | Catalogue public, pages programme des formations, recherche et inscription à la newsletter. |
| Apprentissage | Tableau de bord apprenant, navigation dans les formations, parcours, progression étape par étape, statistiques, certificats et ressources complémentaires. |
| Comptes | Authentification, profils et réglages. |
| Commerce | Essais, abonnements, achat de formations à l'unité et paiement Stripe. |
| Expérience | Design system construit sur shadcn/ui, thèmes clair et sombre, URL bilingues. |
| Exploitation | Administration, processus de traduction et interfaces multilingues. |
| Mesure | Suivi d'événements sur l'acquisition, l'authentification, l'apprentissage et la facturation. |

Le frontend utilise React 19, Vite, Tailwind CSS 4 et shadcn/ui. Firebase fournit l'authentification, le stockage des données (région UE) et les fonctions côté serveur. Stripe gère le paiement et la facturation. Le site public est servi par Cloudflare Pages.

**Livré (29 septembre 2026) :** un onboarding à la première connexion qui recommande la formation la plus pertinente et un rythme réaliste, et l'exercice des droits sur les données en libre-service (export des données et suppression du compte).

## Accès et paiements

Les essais, les abonnements et l'achat de formations donnent à un apprenant des raisons différentes d'avoir accès à une formation. J'ai séparé les informations publiques sur les formations du contenu pédagogique payant, et j'ai lié l'accès aux droits de l'apprenant.

Les changements de facturation sont traités côté serveur. Dans les grandes lignes, un événement de paiement ou d'abonnement met à jour l'état d'accès utilisé par le produit.

L'arbitrage : plus de travail côté serveur et en exploitation, car le paiement, l'état de facturation et l'accès aux formations doivent rester cohérents. En échange, la même expérience de formation peut servir plusieurs modèles commerciaux.

Ce document décrit la décision sans publier les règles d'autorisation, les structures de données internes ni les mécanismes d'accès opérationnels.

## Mesure

J'ai ajouté le suivi d'actions comme l'inscription, le démarrage d'une formation, la progression, la complétion, la recherche et le paiement. Ces événements donnent une base pour étudier le parcours des apprenants. Leur existence ne suffit pas à établir que le produit dispose d'un modèle fiable de conversion ou de rétention.

**Prévu :** définir l'activation plus précisément et étudier le chemin qui va de l'inscription à une première progression significative, puis à la poursuite de l'apprentissage, à la complétion et à l'accès payant. Une mesure d'activation possible serait une progression significative peu après l'inscription, mais la définition et la fenêtre de temps restent à étayer par des données.

## Contenu multilingue

Le support du français et de l'anglais touche le contenu des formations et la navigation autant que les libellés de l'interface. J'ai intégré les processus de traduction aux outils d'exploitation pour que les modifications puissent être gérées dans les deux expériences.

Je traite la langue comme une partie de l'architecture plutôt que comme une couche de présentation. La langue est portée par l'URL et ne change que lorsque l'apprenant la choisit. Chaque texte de l'interface passe par un seul système de traduction. Des tests automatiques font échouer le build en cas de traduction manquante ou de texte écrit en dur, et une suite de tests de bout en bout parcourt le produit dans les deux langues pour repérer les textes dans la mauvaise langue.

Cela ajoute de la maintenance : une modification de formation peut demander de mettre à jour le contenu traduit et la navigation qui l'entoure.

## Observé : l'apprentissage accompagné est la preuve actuelle

Les formations menées à leur terme que j'ai observées jusqu'ici se sont déroulées dans un cadre accompagné ou en direct. Je n'ai pas encore assez d'éléments pour affirmer que des apprenants découvriront une formation seuls, la termineront, retiendront ce qu'ils ont appris et reviendront sur la plateforme.

Il s'agit d'une observation qualitative. Elle n'en identifie pas la cause. Le contenu, l'accompagnement, la diffusion, ou une combinaison des trois, pourraient expliquer l'écart entre usage accompagné et usage autonome.

La prochaine itération doit tester directement l'apprentissage autonome, plutôt que supposer que les résultats obtenus avec un formateur se transposeront à un produit suivi à son rythme.

## Hypothèse : un accompagnement pourrait soutenir l'étude en autonomie

Un Learning Copilot, à l'état de proposition, aiderait les apprenants à choisir un sujet, à obtenir des explications en contexte, à vérifier leur compréhension et à garder une trace des connaissances démontrées.

| Étape | Rôle proposé |
| --- | --- |
| Trouver | Identifier un objectif d'apprentissage pertinent. |
| Apprendre | Aider à éclaircir une notion mal comprise. |
| Vérifier | Demander à l'apprenant de démontrer sa compréhension. |
| Retenir | Garder une trace de ce que l'apprenant a démontré dans le temps. |

L'hypothèse est que cet accompagnement pourrait améliorer l'apprentissage en autonomie et, peut-être, la conversion vers l'offre payante. Aucun de ces deux effets n'a été démontré. Le copilote n'est pas une fonctionnalité livrée.

## Livré : créer le contenu avant d'ajouter la recherche documentaire

Un système de génération augmentée par recherche documentaire (RAG) ne vaut que ce que vaut le contenu qu'il retrouve, et les évaluations ont besoin d'objectifs clairs pour vérifier les réponses. J'ai donc commencé par le contenu.

J'ai écrit un standard de contenu, puis créé selon ce standard les 31 formations du catalogue, en français et en anglais. Chaque formation définit des objectifs pédagogiques, des notions, des prérequis, des idées reçues fréquentes, des sources vérifiées, des évaluations et un livrable que l'apprenant produit sur son propre travail. Un compilateur valide chaque formation par rapport au standard et produit des sorties distinctes pour le catalogue public, le lecteur de cours et une couche de connaissances côté serveur.

**Prévu :** transformer les évaluations en preuves d'apprentissage, préparer des exemples d'évaluation, puis construire et évaluer la recherche documentaire et l'aide en contexte. Il s'agit de travaux prévus. Ce texte n'affirme pas qu'un jeu de données d'évaluation ou un système d'IA est déjà terminé.

## Ce que je changerais

- **Définir l'activation plus tôt.** Décider à quoi ressemble une première progression significative, puis tester si ce comportement prédit la poursuite de l'apprentissage.
- **Écrire le standard de contenu en premier.** Définir objectifs, prérequis, sources et évaluations avant d'écrire la première formation, comme le font aujourd'hui les 31 formations.
- **Distinguer progression et compréhension.** Marquer une étape comme terminée enregistre une action dans le produit. Cela n'établit pas que l'apprenant a compris le contenu.
- **Tester l'usage autonome plus tôt.** Recruter des apprenants en dehors des formations accompagnées et observer où ils ont besoin d'aide.

## Pour aller plus loin

Une [vue d'ensemble de la plateforme](../architecture/platform-overview.fr.md) est disponible. Des captures d'écran du produit et des études de cas ciblées sur l'accès, la mesure et la structure du contenu sont prévues. Les futurs documents d'évaluation de l'IA dépendront d'expériences et de résultats réels.

Chaque nouveau document sera vérifié sur le plan factuel et relu sous l'angle de la sécurité et de la propriété intellectuelle avant publication. Le code de production, les règles de sécurité, les données des utilisateurs et le contenu complet des formations payantes restent privés.

[Retour au Product Lab](../README.fr.md) | [Module](https://bymodule.io) | [Alex Dionisio](https://github.com/alxdionisio)
