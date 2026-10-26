# 002 : Le back-end est un service géré (Firebase et Cloud Functions), pas un serveur sur mesure

*English version: [002-managed-backend-firebase.md](002-managed-backend-firebase.md)*

- **Date :** 2026-03-13 (premier commit du projet ; rédigée en octobre 2026)
- **Statut :** Adoptée
- **Domaine :** plateforme

## Contexte

Quand j'ai commencé Module en mars 2026, je le construisais seul, à côté d'autres activités, sans budget d'infrastructure. La plateforme avait besoin dès le premier jour de ce qu'il faut à tout produit de formation payant : la connexion (lien par email et Google), des rôles (apprenant, administrateur), la progression de chaque apprenant, le paiement, et les obligations liées aux données personnelles (export, suppression). Rien de tout cela ne fait la différence de Module, et chaque heure passée à faire tourner un serveur est une heure de moins pour les formations. Ce que je choisissais devait aussi continuer à fonctionner, en sécurité, sans que personne ne s'en occupe pendant des semaines. C'est d'ailleurs ce qui s'est passé : le projet a été mis de côté après une première version, puis repris en septembre 2026.

## Options

| Option | Pour | Contre |
| --- | --- | --- |
| A. Un back-end sur mesure (serveur d'API et base relationnelle sur un VPS ou une plateforme d'hébergement) | Maîtrise complète ; données relationnelles faciles à interroger ; aucune dépendance au modèle de données d'un fournisseur | Un serveur à sécuriser, mettre à jour, surveiller et sauvegarder ; connexion et sessions à construire ; un coût mensuel fixe dès le premier jour |
| B. Firebase : authentification gérée, base de documents protégée par des règles de sécurité, et fonctions serveur pour ce qui ne doit pas tourner dans le navigateur | Connexion, données et fonctions hébergées par le fournisseur ; paiement à l'usage, proche de zéro à faible volume ; sécurité écrite sous forme de règles testables | Dépendance au modèle de données et au langage de règles d'un fournisseur ; une base de documents se prête mal aux requêtes de reporting ; le coût suit les lectures et les écritures, donc un modèle de données négligé coûte de l'argent |
| C. Un autre back-end géré, bâti sur une base relationnelle | Le même avantage « sans serveur », avec du SQL | Des compromis proches de B pour ce projet, sans avantage décisif |

## Décision

Option B. Le critère qui a tranché : **la plateforme doit tourner en sécurité sans personne dédiée, donc tout ce qui n'est pas propre à Module s'achète comme un service au lieu de se construire.**

La répartition, dans ses principes :

- **Le navigateur** gère l'interface et ne lit que ce que les règles de sécurité autorisent pour la personne connectée.
- **Les règles de sécurité** décident qui peut lire ou écrire chaque donnée. Le contenu payant des formations est derrière elles et n'est jamais livré dans les pages publiques.
- **Les fonctions serveur** (23 en octobre 2026, hébergées à Paris) prennent en charge tout ce qui demande un secret ou doit être fiable : le paiement et les notifications du prestataire de paiement, les changements de rôle, les certificats, les emails transactionnels et de suivi, l'export des données et la suppression de compte, ainsi que les nettoyages programmés qu'impose la politique de confidentialité.
- **Le front-end est un site statique** servi par un CDN, séparé du back-end : les pages publiques restent rapides et indexables quoi qu'il arrive côté serveur.

## Conséquences

- **Rend possible :** une seule personne livre le paiement, les comptes, les certificats et les droits sur les données sans exploiter de serveur. Depuis octobre 2026, un projet de préproduction séparé reproduit la production, et le déploiement des fonctions en production demande une approbation explicite.
- **Coûte et ferme :** le modèle de données et le langage de règles appartiennent au fournisseur : partir serait une migration, pas un simple changement. Le reporting demande du travail en plus, car la base ne répond pas à des requêtes relationnelles à la volée. Et comme la facture suit les lectures et les écritures, la conception des données compte plus que la taille d'un serveur : une revue des coûts en octobre 2026 a trouvé des dépenses évitables, corrigées depuis, et un point à suivre sur la fréquence d'écriture de la progression des apprenants.
- **Demande de la rigueur :** les règles sont testées sur un émulateur, les secrets sont rangés dans un gestionnaire de secrets plutôt que dans le code, et chaque déploiement en production est vérifié contre le bon projet.
- **À surveiller :** le coût d'infrastructure par apprenant actif, et la fréquence à laquelle une question produit ne trouve pas de réponse sans exporter les données. Je regarderai les deux à la publication des premiers chiffres trimestriels de revenus dans [metrics](../metrics/README.fr.md).

## Revue

*Pas encore revue. Prévue avec les premiers chiffres trimestriels de revenus.*
