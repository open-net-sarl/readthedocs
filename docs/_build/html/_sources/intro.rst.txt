########################
Introduction
########################

===========================================
Cadre de l'étude
===========================================

Cette documentation est établie dans le cadre de mon travail de diplôme de `l'Ecole Supérieure d'Informatique de Gestion <http://www.esig-jura.ch>`_ de `Delémont <https://en.wikipedia.org/wiki/Delémont>`_, et porte sur le fonctionnement logistique du système ERP Odoo V11e.

Etudier le fonctionnement logistique d'un système ERP et proposer des solutions d'amélioration nécessite une expérience terrain importante, sachant que l'équivalent sur un corps humain reviendrait à étudier l'ensemble du système sanguin, probablement quelques mécanismes du système nerveux, voire le système limphatique.

Longtemps, on a par exemple soigné la fièvre par `des saignées <https://fr.wikipedia.org/wiki/Saignée_(médecine)>`_, jusqu'au jour où on s'est aperçu que la situation du malade se dégradait plus qu'elle ne s'améliorait.


    .. figure:: ./img/Pratique_d'une_saignee.jpg
        :alt: Pratique d'une saignée
        :scale: 70%
        :align: center

        `Pratique d'une saignée (Crédit Wikipedia) <https://commons.wikimedia.org/wiki/File:Pratique_d'une_saignée.jpg>`_

Les systèmes de gestion ERP d'aujourd'hui, que ce soit le plus imposant `SAP <https://www.sap.com/index.html>`_ ou `le "petit" Odoo <https://www.odoo.com>`_, ne sont pas vraiment encore intelligents. Ils appliquent des schémas préconçus (paramètrage) suite à des actions d'utilisateurs ou de job réguliers. Quelques algorithmes bien pensés permettent aux différents reponsables métiers d'obtenir une vue en temps réel sur la situation de l'entreprise.

Mais lorsque le système ERP subit une "poussée de fièvre", il est important de rechercher la cause profonde du problème, et d'appliquer la solution avec tact et parcimonie, surtout lorsque le système est en production. La saignée doit être évitée à tout prix. Cela est également le cas lorsque des fonctionnalités doivent être ajoutées au système.

La tâche est donc vaste et hardue.

=============================================
Déroulement de l'étude
=============================================

Le mandat du travail de diplôme porte sur l'analyse du système logistique "tel quel", sur l'établissement de propositions d'améliorations en relation avec le manufacturing complexe, et le codage d'un ou plusieurs modules de correction.

A mon sens, la bonne pratique en terme d'implémentation et d'adaptation d'un ERP à une entreprise est :
    #. Etude et compréhension de la philosophie du système ERP
    #. Etude et compréhension des besoins du client en terme de gestion, au sens large
    #. Identification des objets du système ERP répondant aux besoins
    #. Vérifier si les flux entre les objets répondent aux exigences

Si ce n'est pas le cas, nous aurons le choix entre :
    #. Rester dans la philosophie du système,
        - en proposant un flux alternatif standard au client, ou
        - adapter le système par du paramètrage
    #. Adapter / Raccourcir le flux
        - par du code sur un user-exit
        - par un module de code dédié

Vu l'étendue d'un système tel que SAP, il est rare de devoir coder au coeur du système, mais cela est plus fréquent en périphérie. Sur un système tel que Odoo, cela est plus fréquent, vu que le nombre d'objets à disposition est plus restreint.

Dans tous les cas, on privilériera autant que faire ce peu d'éviter de coder - même si cela est parfois tentant. Ces ajouts de code n'étant pas connus de l'éditeur, il peuvent fragiliser la cohérence du système, et certainement ralentir les montées de version, puisque l'ensemble des flux devront être revalidé.

Ne pas coder implique par contre une connaissance parfaite et large des capacités de l'outil en terme de paramètrage. Egalement, on ne peut pas se satisfaire d'un flux qui fonctionne parfaitement... Une modification peut avoir provoqué un dommage collatéral sur le flux voisin.

Dans le cadre de ce travail, **je vais donc d'abord m'appliquer à étudier et à m'imprégner de la philosophie** de fonctionnement de Odoo.

N'ayant pas encore une connaissance approfondie de l'outil, cette phase **est à risque** du point de vue **du délai** des phases de projet, puisque, vu ce qui a été évoqué à l'instant, il n'est **pas question de proposer** un module de correction, **sans avoir la certitude** que du paramètrage pourrait corriger la situation.

Une autre question se pose : si la phase de compréhension se prolonge, je ne pourrai pas montrer de code lors de la défense. A mon sens, ceci n'est pas grâve puisque appuyer du code à un autre endroit que la cause première du problème, revient à construire une magnifique villa sur une falaise qui s'érode. Je m'en tiendrai dans ce cas aux plans d'architecte.

    .. figure:: ./img/maison_sur_falaise.jpg
        :alt: Maison sur une falaise qui s'érode en Californie
        :scale: 70%
        :align: center

        `Californie: l'érosion d'une falaise oblige des familles à évacuer leurs habitations (Crédit RTBF) <https://www.rtbf.be/info/insolites/detail_californie-l-erosion-d-une-falaise-oblige-des-familles-a-evacuer-leurs-habitations?id=9197405>`_


======================================================
La logistique, les opérations, la fabrication
======================================================

Dans le cadre de ce travail, nous vérifierons si le système Odoo permet à une entreprise manufacturière de fournir des biens industriels à un client, en s'approvisionnant en matière premières, en les transformant, en les stockant et en les livrant.

Nous nous intéresserons principalement aux flux, à la transformation et au stockage des articles. Nous regrouperons l'ensemble de ces activités sous le terme générique d'**opérations**. Nous associerons le terme **fabrication** ou **manufacturing** aux opérations de transformation d'éléments vers un composé de nature différente.

Avant de nous lancer dans l'étude à proprement parler, nous allons encore définir quelques éléments de compréhension. 

.. admonition:: On ne fait pas d'omelette sans casser des oeufs !

   Arrêtons-nous quelques instants sur cette `locution populaire <https://fr.wiktionary.org/wiki/on_ne_fait_pas_d’omelette_sans_casser_des_œufs>`_, qui signifie que lorsque on veut entreprendre quelque chose, il faut en accepter les risques. Cela s'applique bien entendu à la fabrication et à la probabilité que le résultat final ne soit pas toujours celui escompté.


    .. figure:: ./img/oeuf_casse.jpg
        :alt: Oeuf casse
        :scale: 40%
        :align: center

        `Oeuf cassé (Crédit bioalaune.com) <https://www.bioalaune.com/fr/actualite-bio/12067/non-au-gaspillage-alimentaire-cinq-astuces-utiliser-blancs-doeufs>`_


   Intéressons nous maintenant à la forme littérale de cette phrase...

    - On apprend tout d'abord que pour pour fabriquer une omelette, il faut des oeufs. 
    
    On ne nous dit pas toutefois combien d'oeufs sont nécessaire, ni le temps de cuisson pour que l'on puisse parler d'omelette. En cuisine, la méthode d'obtention d'une omelette s'appelle ``une recette``.

    
    .. figure:: ./img/recette_omelette.png
        :alt: Recette d'une omelette simple
        :scale: 70%
        :align: center

        `Recette d'une omelette simple (Crédit https://www.cuisineaz.com) <https://www.cuisineaz.com/recettes/omelette-simple-56045.aspx>`_

    On réalise que pour cuisiner (fabriquer) une omelette de qualité et de taille satisfaisante pour **une personne**, il faut des ingrédients dans **une quantité bien déterminée**. 
    D'autre part, la préparation des ingrédients se réalise en **deux étapes distinctes** impliquant des ``opérations`` précises (Etape 1 : Battez..., Etape 2 : Faites chauffer...).

    Cette recette est probablement suffisante pour le repas du soir, mais dans un milieu industriel, elle est insuffisamment précise. En effet, on obtiendra une omellette de taille différente selon la taille des oeufs.

    En termes industriels, on parlera de ``fabrication en process`` dans le cas où le produit est obtenu sur la base d'une formule ou d'une recette, et que les ingrédients qui le compose ne peuvent plus être facilement dissociés après la transformation. Par opposition, on parlera de ``fabrication discrète`` lorsque le produit obtenu peut être facilement touché, vu ou compté. 

    Dans l'étude, nous nous intéresserons **uniquement à la fabrication discrète**, qui traite de produits tels que montres, voitures, machines, etc.
    
    Pour fabriquer un objet discret, nous parlerons de ``nomenclatures`` (Bill of Materials - BOM en anglais), qui précisent que pour fabriquer 1 voiture, il faut :
        - 1 chassis,
        - 1 moteur et
        - 4 roues.

    et de ``gammes de fabrication`` ou ``gammes opératoires`` (routings en anglais), qui définissent la séquence des opérations d'usinage/assemblage, les ``ressources`` nécessaires (machines, outils, main d'oeuvre, qualitification, énergie, fluides, etc.).

    Une ``nomenclature multi-niveaux`` est le résultat de nomenclatures "imbriquées". Par exemple, pour produire une voiture, il faut un moteur, lui même composé d'un bloc moteur et de 4 pistons. On comprendra ainsi qu'avant de pouvoir assembler la voiture, il aura fallu au préalable obtenir de l'acier pour réaliser les 4 pistons, puis assembler les pistons et le bloc pour former le moteur, et finalement assembler le moteur, les roues et le chassis.

    Cette séquence est jalonnée de contraintes, de nature temporelles, physiques (volumes, quantité disponible, ressources) et financières (cash flow).  

    On comprendra également que l'on ne produira pas forcément les moteurs dans les mêmes quantités (``taille de lot``) et au même endroit que les voitures. Ainsi les notions de ``stockage``, d' ``emplacement de stock``, d' ``entrepôt`` et de ``transport`` interviennent.

    D'autre part, une entreprise maximisera ses ventes en proposant ses produits à sa clientèle, à un délai acceptable par celle-ci. Elle pourra être temptée d'anticiper les besoins des clients et de produire et stocker massivement. Mais dans ce cas, si les prévisions s'avèrent surévaluées, le stock deviendra obsolète et ne pourra plus être vendu.

    Pour éviter cela, on recherchera constamment à minimiser les valeurs en stock, en standardisant les produits et en approvisionnant au dernier moment. Citons encore deux techniques fondamentales d'approvisionnement :

        - ``le flux poussé`` : dans ce contexte, une prévision de vente va engendrer l'approvisionnement de tous les composants nécessaires, lesquels vont remonter progressivement vers les stocks de produits semi-finis, puis vers les stocks de produits finis. Dans le cas de notre omelette, si le délai de fabrication est de trois jours, il faudra prévoir ce que nous voulons manger dans trois jours, et nous y tenir ! 

        - ``le flux tiré`` : dans cette situation, le réapprovisionnement n'a lieu que lorsque le stock a été consommé. Dans le cas de notre omelette, cela signifie dans nous maintenons un petit stock d'oeufs (``stock intermédiaire``), et que lorsque nous les utilisons pour réaliser une omelette, nous recomplétons ce stock. On parlera également de ``juste-à-temps`` lorsque le stock arrive au moment de sa consommation. Notre omelette est cuisinée juste-à-temps pour le repas du soir !

    Bon appétit !  

    
        .. figure:: ./img/omelette.jpg
            :alt: Omelette
            :scale: 60%
            :align: center

            `Omelette (Crédit bbcgoodfood.com) <https://www.bbcgoodfood.com/recipes/1669/ultimate-french-omelette>`_





       

========================
Licence
========================

.. raw:: html
   :file: licence.html