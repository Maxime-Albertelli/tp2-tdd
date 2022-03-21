# <img src="https://raw.githubusercontent.com/IUTInfoAix-M2105/Syllabus/master/assets/logo.png" alt="class logo" class="logo"/> Artisanat logiciel et qualité de développement

### IUT d’Aix-Marseille – Département Informatique Aix-en-Provence

* **Ressource:** [R2.03](https://cache.media.enseignementsup-recherche.gouv.fr/file/SPE4-MESRI-17-6-2021/35/5/Annexe_17_INFO_BUT_annee_1_1411355.pdf)
* **Responsables:** 
    * [Sébastien NEDJAR](mailto:sebastien.nedjar@univ-amu.fr)
    * [Cyril Pain-Barre](mailto:cyril.pain-barre@univ-amu.fr)
* **Besoin d'aide ?**
    * Consulter et/ou créér des [issues](https://github.com/IUTInfoAix-R203/tp1-git/issues).
    * [Email](mailto:sebastien.nedjar@univ-amu.fr) pour une question d'ordre privée, ou pour convenir d'un rendez-vous physique.

## Aperçu du TP et objectifs d'apprentissage

L'objectif premier de ce TP est de vous familiariser avec tous les nouveaux outils qui seront mis en oeuvre pendant ce cours. Ce TP est à la fois une découverte des tests unitaires et de leur mise en pratique en Java. Vous aurez accès également à du matériel plus approfondi et quelques idées pour vous aider à aller plus loin.

Ce TP est une libre adaptation du [TP1 du module M2105](https://github.com/IUTInfoAix-M2105/tp1_19et20).


## TP 2 : Découverte de l'environnement de travail, des outils et premiers programmes en Java


### Création de votre fork

Vous connaissez déjà les bases de Git. Si ce n'est pas le cas, il vous faudra réaliser le [TP Git](https://github.com/IUTInfoAix-R203/tp1-git).

Cela vous sera indispensable pour commencer à travailler sur vos TP. Comme vous allez le découvrir le rendu et le suivi de votre travail passeront directement par GitHub. 

La première chose à faire est de créer un fork de ce dépôt. Pour ce faire, rendez-vous sur le lien suivant : 

https://classroom.github.com/a/Lr1twuc_

GitHub va vous créer un dépôt contenant un fork du dépôt 'IUTInfoAix-R203/tp2-tdd' et s'appellant 'IUTInfoAix-R203/tp2-votreUsername'. 
Vous apparaîtrez automatiquement comme contributeur de ce projet pour y pousser votre travail. Sachez qu'un robot récupérera automatiquement votre code après chaque *push* pour vérifier que les tests passent et calculer votre taux d'accomplissement du TP.

### Découverte et prise en main de l'IDE

Avant de commencer le TP à proprement parler, lisez la page ["Découverte et prise en main de l'IDE"](https://github.com/IUTInfoAix-R203/tp2-tdd/blob/main/decouverte_et_prise_en_main_IDE.md).

### Mode opératoire du TP (Workflow)

Maintenant que vous savez utiliser Git en ligne de commande, que vous avez forké avec le lien classroom et importé le TP dans votre IDE, vous êtes en capacité de travailler sur vos exercices.

Ce TP est conçu pour vous faire découvrir les tests unitaires et le **Test Driven Development (TDD)**, c'est à dire le développement conduit par les tests.

Le TDD est une méthode de conception émergente selon laquelle la conception apparaît au fur et à mesure du développement en encourageant une meilleure compréhension du problème **en commençant à écrire les tests avant le code applicatif**. Pour le développeur, les tests vont constituer une spécification technique exécutable et vérifiable à tout moment. Ainsi en rajoutant des tests, le développeur converge progressivement à la fois vers une spécification plus fine et un code fonctionnel associé.

Le workflow du TDD est souvent décrit par le triptyque "RED, GREEN, REFACTOR" (figure empruntée au site [ministryoftesting](https://www.ministryoftesting.com)) :

![](src/main/resources/assets/graphic_tdd.png)

Nous vous proposons de suivre ce workflow particulier pour résoudre vos exercices progressivement et en consolidant au fur et à mesure un filet de sécurité qui vérifiera que votre code continue à bien faire ce qu'il doit. Pour vous faciliter la tâche pour ce TP, les tests vous sont donnés pour vous habituer à cette méthodologie sans trop de douleur.

#### Première exécution d'un test

Avant de vous présenter plus précisément ce que vous devez réaliser dans le contexte du TDD, commençons par exécuter un premier test, presque aussi inutile que notre classe `App` car il est censé ne jamais échouer, mais nous permettant de vérifier que les tests sont fonctionnels.

Ouvrez le fichier `AppTest.java`, présent dans `src/test/java/fr/univ_amu/iut`.

Il contient un seul test `testApp()` qui s'assure que `true` est toujours vrai...
La classe `AppTest` devrait être reconnue comme une classe de tests unitaires et apparaître avec l'icône ![Icône classe de test](src/main/resources/assets/idea_test_class.png) ajoutant un triangle rouge à celle des classes exécutables.

Pour exécuter ce test, utiliser l'icône vert ![run test](src/main/resources/assets/idea_run_single_test.png) (ou comme ici  ![mark method test passed](src/main/resources/assets/idea_test_method_mark_passed.png) ou encore ![mark method test failed](src/main/resources/assets/idea_test_method_mark_failed.png), voir ci-après) dans la marge à gauche du code de la méthode, et sélectionner Run 'testApp()'. En bas de la fenêtre devrait s'afficher le résultat du test passé avec succès ayant une marque verte ![test passed image](src/main/resources/assets/idea_test_passed.png).

Et dans la marge du code de la méthode `testApp()` devrait apparaître l'icône ![mark method test passed](src/main/resources/assets/idea_test_method_mark_passed.png).

Quand une classe de test possède plusieurs méthodes de test, on peut les exécuter tous en cliquant sur l'icône ![run test class image](src/main/resources/assets/idea_run_tests_class.png) puis en choisissant d'exécuter la classe entière.

Si un test échoue, son résultat sera écrit en rouge avec le marqueur ![run test failed](src/main/resources/assets/idea_test_failed.png) et la marge du code de la méthode correspondante aura l'icône ![mark method test failed](src/main/resources/assets/idea_test_method_mark_failed.png). Un double clic sur le test vous ramènera sur son code.

Certains tests peuvent être momentanément désactivés car leur méthode est préfixée de l'annotation `@Disabled`. Dans ce cas, le test est ignoré et apparaît avec la marque ![run test ignored](src/main/resources/assets/idea_test_ignored.png). Pour activer le test, il faut mettre en commentaire l'annotation `@Disabled` ou la supprimer.

Enfin, quand il existe plusieurs classes de test regroupées comme ici dans l'arborescence `src/test/java`, il est possible de faire exécuter la totalité de tous les tests (non désactivés) en faisant un clic droit sur le dossier java ![run all tests start point](src/main/resources/assets/idea_run_all_tests.png) et en choisissant Run 'All Tests'...

#### Étapes du cycle principal

Au cours du TP, vous devrez donc opérer en TDD. Chaque exercice sera accompagné d'au moins une classe de test, dont tous les tests sont initialement désactivés. Pour réaliser l'exercice vous devrez suivre cycliquement les étapes suivantes (indiquées dans la figure précédente, illustrant le TDD) : 

1. **RED :** Dans cette étape, vous devez activer un test en enlevant le `@Disabled` devant la méthode de test (ou en la décommentant). Une fois le test activé, vous devez le lancer pour vérifier qu'il échoue. Un test qui n'échoue jamais (comme celui de `AppTest`) ne teste rien donc il ne sert à rien.

1. **GREEN :** Ici vous devez écrire le moins de code possible pour faire passer le test en question. Quand vous pensez avoir terminé, vous relancez le test en question pour vérifier que le code est juste. Si tel est le cas, vous lancez tous les autres tests pour vous assurer que votre implémentation n'a rien cassé.

1. **REFACTOR :** Maintenant que votre couverture de test est au vert, vous pouvez transformer votre code pour le nettoyer, le restructurer et l'améliorer sans en changer le comportement. Pendant cette étape, les tests doivent être continuellement au vert. Ils jouent le rôle de filet de sécurité pour éviter l'introduction d'une régression dans le code. Quand tout est terminé vous pouvez redémarrer le cycle avec un prochain test.

**À chaque fin de cycle**, vous devez commiter votre travail sur votre dépôt Git local et le pousser sur votre fork sur GitHub. Vous terminez un exercice lorsque tous les tests y sont activés et passent sur votre dépôt distant.

