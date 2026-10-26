# Module Product Lab

*English version: [README.md](README.md)*

[Module](https://bymodule.com) est une plateforme de formation pour les Product Managers, écrite pour des praticiens qui construisent des produits numériques. Je l'ai conçue et construite dans le cadre de [Module](https://bymodule.io), mon activité indépendante de produit numérique.

Ce dépôt documente une sélection de décisions produit, d'arbitrages techniques et d'enseignements tirés de la construction de la plateforme. Le code source de production et le contenu des formations payantes restent privés.

## Naviguer dans ce dépôt

| Section | Ce que vous y trouvez |
| --- | --- |
| [Roadmap](ROADMAP.fr.md) | Now, Next et Later, avec un statut sur chaque élément. Revue chaque mois. |
| [Changelog](CHANGELOG.fr.md) | Une ligne par livraison de la plateforme depuis la publication de ce lab, le 29 septembre 2026. |
| [Décisions](decisions/001-content-as-tested-structured-files.fr.md) | Une décision par fichier : contexte, options, décision, conséquences. [001](decisions/001-content-as-tested-structured-files.fr.md) le contenu en fichiers testés, [002](decisions/002-managed-backend-firebase.fr.md) un back-end géré, [003](decisions/003-pricing-before-launch.fr.md) la grille de prix avant le lancement. Le [modèle](decisions/000-template.fr.md) sert de point de départ. |
| [Playbooks](playbooks/01-frame-a-learning-platform.fr.md) | Des guides reproductibles pour les Product Managers. |
| [Chiffres](metrics/README.fr.md) | Ce que je publie, d'où viennent les chiffres, et quand. |
| [Architecture](architecture/platform-overview.fr.md) | L'organisation de la plateforme, au niveau de l'architecture produit. |
| [Étude de cas](case-studies/01-building-bymodule-from-0-to-1.fr.md) | Construire Module de 0 à 1. |
| [Discussions](https://github.com/byModule/bymodule-product-lab/discussions) | Idées de formations, retours sur la plateforme, questions sur la méthode. |

Chaque document existe en anglais, avec sa version française à côté (`.fr.md`).

## Ce qui a changé (octobre 2026)

À sa publication en septembre, ce lab contenait une étude de cas et une vue d'ensemble de l'architecture. Depuis octobre 2026, il contient aussi :

- **Des chiffres.** Les chiffres d'usage chaque mois et les revenus chaque trimestre, à commencer par le fichier d'usage d'octobre, le 2 novembre 2026. La [page des chiffres](metrics/README.fr.md) explique ce qui est compté et d'où cela vient.
- **Une roadmap publique**, avec les mêmes statuts que le reste du dépôt.
- **Un changelog** des livraisons de la plateforme.
- **Des décisions et des playbooks**, en commençant par un de chaque.
- **Une invitation à donner votre avis** dans les [Discussions](https://github.com/byModule/bymodule-product-lab/discussions) : idées de formations, retours sur la plateforme, questions sur la méthode. Les retours qui modifient la roadmap y sont cités.

## Le produit

La plateforme livrée, décrite dans la [première étude de cas](case-studies/01-building-bymodule-from-0-to-1.fr.md), comprend :

- Un catalogue de 31 formations, chacune créée en français et en anglais selon un standard de contenu structuré.
- La découverte des formations, des pages programme avec objectifs pédagogiques et livrables, et une recherche.
- Des comptes, un tableau de bord apprenant, des parcours et une progression étape par étape.
- Des statistiques d'apprentissage et des certificats.
- Une expérience produit et pédagogique en français et en anglais, la langue étant portée par l'URL et modifiée uniquement par l'apprenant.
- Un design system construit sur shadcn/ui, avec thème clair et thème sombre.
- Un accès d'essai, des abonnements et l'achat de formations à l'unité.
- Le paiement Stripe et des traitements de facturation côté serveur.
- La mesure d'audience produit, l'inscription à la newsletter et des outils d'administration.

L'application utilise React 19, Vite, Tailwind CSS 4 et shadcn/ui, avec Firebase Authentication, Firestore (région UE) et Cloud Functions. Stripe gère les paiements, et le site public est servi par Cloudflare Pages. Vitest et Playwright couvrent les tests unitaires et de bout en bout.

**En ligne (29 septembre 2026) :** un onboarding à la première connexion qui recommande la formation la plus pertinente et un rythme réaliste, et l'exercice des droits sur les données en libre-service (télécharger toutes ses données personnelles, supprimer son compte avec un délai de grâce).

Ces descriptions reposent sur mon propre compte rendu du produit. Ce dépôt ne contient pas encore de vérification indépendante en production ni de résultats d'usage publiés.

## Mon rôle

Je suis Alex Dionisio, Senior Product Manager et fondateur de Module. J'ai défini le produit, conçu les parcours des apprenants, construit l'application et les intégrations côté serveur, et créé le contenu pédagogique. Je m'occupe aussi des prix, de la mesure d'audience, des processus de traduction et des évolutions du produit.

Module est à la fois mon activité de produit numérique ([bymodule.io](https://bymodule.io)) et le nom de la plateforme de formation ([bymodule.com](https://bymodule.com)). Ce Product Lab documente la plateforme de formation.

## Une décision de la première version

La plateforme propose des essais, des abonnements et l'achat de formations. Les descriptions publiques des formations et le contenu payant n'ont pas le même rôle : j'ai donc séparé la découverte de l'accès au contenu pédagogique. L'[étude de cas](case-studies/01-building-bymodule-from-0-to-1.fr.md#accès-et-paiements) explique cet arbitrage produit dans les grandes lignes.

## Ce que j'ai observé

Les formations menées à leur terme que j'ai observées jusqu'ici se sont déroulées dans un cadre accompagné ou en direct. Cela ne permet pas de dire si les apprenants termineront les formations seuls, retiendront ce qu'ils apprennent ou reviendront sans formateur.

Il s'agit d'une observation qualitative issue de mon travail sur le produit. Je ne publie ici aucun chiffre de complétion, de rétention ou de conversion.

## Ce que j'étudie

**Hypothèse :** un accompagnement contextuel et des vérifications de compréhension pourraient aider les apprenants à étudier en autonomie. Un Learning Copilot est une piste proposée pour le tester. Ce n'est pas une fonctionnalité livrée.

La séquence d'apprentissage proposée :

1. **Trouver :** identifier quoi apprendre pour un objectif donné. La recommandation de l’onboarding en est la première étape (en ligne).
2. **Apprendre :** obtenir de l'aide sur une notion mal comprise.
3. **Vérifier :** démontrer sa compréhension au regard d'un objectif pédagogique.
4. **Retenir :** garder une trace des connaissances démontrées dans le temps.

**Livré :** avant tout travail de recherche documentaire automatisée, j'ai écrit un standard de contenu et créé les 31 formations du catalogue selon ce standard. Chaque formation définit des objectifs pédagogiques, des notions, des prérequis, des idées reçues fréquentes, des sources vérifiées et des évaluations, en français et en anglais.

**Prévu :** transformer les évaluations en preuves d'apprentissage, préparer un jeu de données d'évaluation, puis mettre en place la recherche documentaire et évaluer un copilote. Ce sont des priorités de développement, pas des résultats validés.

## Lire l'étude de cas

[Construire Module de 0 à 1](case-studies/01-building-bymodule-from-0-to-1.fr.md) couvre la première version, les décisions qui l'ont façonnée et ce que je changerais.

La [vue d'ensemble de la plateforme](architecture/platform-overview.fr.md) décrit l'organisation de la plateforme, au niveau de l'architecture produit.

Des captures d'écran du produit et d'autres décisions sont prévues. Elles seront ajoutées après vérification de leurs fondements factuels et de leur caractère publiable.

## Comment lire les statuts

| Statut | Signification |
| --- | --- |
| Livré (Shipped) | Décrit par son auteur comme disponible dans le produit en ligne. |
| En cours (In progress) | Construit ou en construction, pas encore en ligne. |
| Observé (Observed) | Une observation rapportée, avec ses éléments de preuve et ses limites. |
| Hypothèse (Hypothesis) | Une explication ou un bénéfice supposé, qui reste à tester. |
| Prévu (Planned) | Un travail envisagé pour une prochaine itération. |

Les documents publics excluent le code de production, les identifiants, les règles de sécurité, les données des utilisateurs, les formations payantes complètes et les détails opérationnels qui pourraient fragiliser le service.

## Liens

- [Module : la plateforme de formation](https://bymodule.com)
- [Module : l'activité de produit numérique](https://bymodule.io)
- [Alex Dionisio sur GitHub](https://github.com/alxdionisio)

## Licence

La documentation de ce dépôt est publiée sous licence [Creative Commons Attribution 4.0 International](LICENSE) (CC BY 4.0). Le code source de la plateforme n'est pas public et ne fait pas partie de ce dépôt.
