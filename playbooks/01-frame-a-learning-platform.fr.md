# Playbook 01 : cadrer une plateforme de formation avant de la construire

*English version: [01-frame-a-learning-platform.md](01-frame-a-learning-platform.md)*

*Temps de lecture : 10 min · Temps d'application : une demi-journée · Outils : aucun en particulier*

**Ce que vous aurez à la fin** : une page de cadrage qui dit pour qui vous construisez, ce que ces personnes doivent savoir faire après, ce que vous refusez de devenir, et comment vous saurez que ça marche. Le contenu, le code, le design et la communication en découlent.

---

## Pourquoi ce playbook

J'ai commencé Module le 13 mars 2026 avec un dépôt vide. Au 12 octobre 2026, la branche principale compte 705 commits. Avec le recul, ce qui tranche le plus de questions n'est pas une décision technique : c'est une page de cadrage, `PRODUCT.md`, qui tient en moins de 400 mots.

Cette page sert de référence quand une décision n'est pas évidente : faut-il ajouter une formation « tendance », un compte à rebours sur une offre, un extrait gratuit plutôt qu'un cours complet ? La réponse est souvent déjà écrite. Voici comment la construire.

## 1. Écrire le job à faire, pas le sujet

Un sujet (« l'IA pour les PM ») ne dit pas quoi construire. Un job à faire, si.

Formulez-le ainsi : **« [Qui] veut [obtenir quoi] parce que [situation], et repart avec [livrable concret]. »**

Pour Module :

> Des Product Managers (et des fondateurs, PO, designers de produits numériques) veulent comprendre l'IA et la tech assez bien pour **décider, challenger les ingénieurs et livrer**, parce qu'on leur demande des arbitrages qu'ils ne peuvent pas toujours vérifier. Ils repartent de chaque formation avec **un livrable construit sur leur propre produit**.

Le morceau qui compte le plus : « un livrable construit sur leur propre produit ». C'est lui qui impose la structure des leçons et le format des exercices.

**Test** : si votre phrase marche aussi bien pour un concurrent, elle n'est pas finie.

## 2. Nommer ce que vous refusez de devenir

C'est l'étape la plus souvent sautée. Listez trois ou quatre produits ou formats que vos utilisateurs connaissent et que vous ne voulez pas être, en précisant pourquoi.

Pour Module :

| Anti-référence | Ce que cela exclut concrètement |
|---|---|
| Le LMS d'entreprise daté | Une interface grise, lourde, pilotée par des formulaires |
| La page de vente « gourou » | Comptes à rebours, promesses de revenus, faux témoignages, avalanches de bonus |
| Le SaaS IA générique | Dégradés violets, « AI-powered » partout, grilles d'icônes interchangeables |
| Le catalogue vidéo | Des centaines de vidéos, des étoiles, aucun livrable |

Chaque ligne devient une règle de design, de contenu ou de communication. « Pas de faux témoignages » veut dire : on ne cite un retour qu'avec l'accord de son auteur. « Aucun livrable » veut dire : pas de formation sans livrable.

## 3. Choisir l'unité de valeur

Qu'est-ce que l'apprenant obtient vraiment ? Des heures de vidéo ? Un accès ? Un certificat ? Une capacité ?

Pour Module, l'unité est **la capacité** : une formation porte sur ce que l'apprenant saura faire (spécifier une fonctionnalité IA, lire une architecture, interroger des données, mener un test A/B), et se termine par un livrable. Trois conséquences :

1. **Le catalogue se lit comme une liste de compétences**, pas comme un sommaire.
2. **La durée devient secondaire** : ce qui compte, c'est que la capacité soit acquise et le livrable produit.
3. **La valeur se lit dans le livrable**, pas dans le volume de contenu.

**Test** : relisez vos trois premiers titres. Un PM peut-il dire à son manager « j'ai suivi ça, voilà ce que j'ai produit » ?

## 4. Définir la réussite, à deux niveaux

Une phrase pour le visiteur, une pour l'apprenant. Elles deviennent vos indicateurs.

> **Visiteur** : il comprend en quelques secondes que la plateforme est faite pour lui, commence le premier cours offert, le termine, et continue.
>
> **Apprenant** : il progresse sans friction et revient.

De ces deux phrases, je tire les chiffres que je publie chaque mois (visites, inscriptions, complétion du cours offert, achats, retours qualifiés) : voir la [page des chiffres](../metrics/README.fr.md). Le passage de l'inscription à la complétion est celui qui dit si la promesse est tenue.

## 5. Écrire des principes de design (cinq au maximum)

Pas des valeurs : des **règles que l'on peut vérifier sur un écran**. Les miens :

1. **Montrer le livrable, pas les heures.** Chaque écran rend visible le résultat concret.
2. **Une confiance d'expert, sans emphase.** Les affirmations sont précises et vérifiables.
3. **De l'élan.** La prochaine étape est toujours évidente : commencer, continuer, passer à la formation suivante du parcours.
4. **Respecter le temps de l'apprenant.** Court, dense, facile à parcourir, sans remplissage décoratif.
5. **Un système, deux langues.** Le français et l'anglais sont traités à égalité, sans mélange ni approximation.

Le cinquième principe coûte cher : chaque formation existe deux fois, chaque page publique aussi. Je l'ai gardé parce que les PM travaillent souvent dans les deux langues, et qu'un produit à moitié traduit contredit le deuxième principe.

## 6. Décider ce qui est gratuit, et pourquoi

C'est une décision de cadrage avant d'être une décision de prix. La question : **qu'est-ce qui doit être prouvé avant qu'on vous paie ?**

Pour Module, il faut prouver que la promesse « un livrable sur votre propre produit » est tenue. Le premier cours est donc offert en entier : un extrait de quelques minutes ne prouverait rien.

Ce choix a une conséquence directe sur l'onboarding : il faut recommander le bon premier cours, sinon la preuve tombe à plat. D'où quelques questions à la première connexion (rôle, objectif, niveau, temps disponible) avant de proposer une formation.

## 7. Garder la page à côté du code

Un cadrage ne sert que s'il est lu. Le mien est un fichier `PRODUCT.md` placé avec le code de la plateforme. Il est lu :

- par moi, avant un arbitrage de roadmap ;
- par les agents IA avec lesquels je produis le contenu et le code : ils le reçoivent en contexte, ce qui limite les dérives de ton et de périmètre ;
- par toute personne qui relit une formation.

Structure, dans l'ordre :

```
# Product
## Users              le job à faire (étape 1)
## Product Purpose    l'unité de valeur et la réussite (étapes 3 et 4)
## Brand Personality  la voix, en trois adjectifs et deux phrases
## Anti-references    étape 2
## Design Principles  étape 5
## Accessibility      ce qui n'est pas négociable (pour Module : WCAG 2.2 AA, en français et en anglais)
```

Si la page dépasse 400 mots, c'est souvent qu'une question n'est pas encore tranchée.

---

## Ce que je ferais autrement

J'ai écrit `PRODUCT.md` le 1er octobre 2026, alors que les 31 formations du catalogue existaient déjà. Il a surtout servi à cadrer la refonte du design et la suite. Écrit plus tôt, il aurait sans doute évité des allers-retours sur le ton et le périmètre des premières formations. Écrivez-le avant le premier contenu.

## Pour reproduire chez vous : 5 étapes

1. **Écrivez le job à faire** en une phrase, avec le livrable concret à la fin. Vérifiez qu'elle ne marche pas aussi pour un concurrent.
2. **Listez trois anti-références** et, pour chacune, la règle concrète qu'elle impose.
3. **Choisissez votre unité de valeur** et relisez vos trois premiers titres à sa lumière.
4. **Définissez la réussite** en une phrase pour le visiteur et une pour l'apprenant, puis déduisez-en cinq ou six chiffres à suivre.
5. **Décidez ce qui est gratuit** en répondant à « qu'est-ce qui doit être prouvé avant qu'on me paie ? », puis rassemblez le tout dans une page de moins de 400 mots, rangée à côté du code et donnée à chaque personne ou agent qui travaille sur le produit.

## Liens

- La plateforme : [bymodule.com](https://bymodule.com/fr?utm_source=github&utm_medium=repo&utm_campaign=productlab&utm_content=playbook-01)
- La formation qui applique cette démarche à votre propre projet de formation : [Concevoir et lancer une formation en ligne efficace](https://bymodule.com/fr/formations/module-formation-en-ligne?utm_source=github&utm_medium=repo&utm_campaign=productlab&utm_content=playbook-01)
- Décision liée : [001 : le contenu des formations vit dans des fichiers structurés, vérifiés comme du code](../decisions/001-content-as-tested-structured-files.fr.md)

*Une question, un désaccord ? Ouvrez une discussion dans la catégorie « Questions about the method » des [Discussions](https://github.com/byModule/bymodule-product-lab/discussions).*
