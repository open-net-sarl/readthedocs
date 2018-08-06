
###############################
Etudes
###############################

=====================================================
La société fictive "Open Bike SF"
=====================================================

Dans le but d'assurer une certaine **cohérence des tests** à réaliser, nous utiliserons un **jeu de test** basé sur une **société fictive "Open Bike SF (OBSF)"**.

OBSF commercialise des **vélos haut de gamme**, principalement en Europe. Elle a été fondée il y a 5 ans par trois ingénieurs passionnés de cyclisme.

Les grands avantages des vélos OBSF sont :

    - une conception robuste
    - un look sportif et jeune
    - un service après-vente impeccable

Les ventes connaissent une **forte croissance** depuis la création de la société. Ceci nécessite un **suivi constant des ressources** disponibles, notamment du **cash-flow** et de la **disponibilité des produits**. 

Les **vélos de montagne** sont fabriqué entièrement **dans les ateliers de Romont et de Bussigny**. Les **vélos de ville**, par contre, sont **entièrement sous-traités** en Asie en mode "Fabless Manufacturing".

Les dirigeants de OBSF souhaitent acquérir un nouveau système de gestion pour leur entreprise. Ils nous ont contacté avec un cahier des charges précis, en nous demandant d'éviter spécifiquement les points faibles de leur ancien système ERP :  

=====================================================
A) Approvisionnement "Juste-à-temps"
=====================================================

    A1) Le système doit permettre de commander et d'être livré "au plus tard" ou **"juste-à-temps"**, c'est-à-dire au moment précis des besoins de l'ordonnancement. Ceci permet notamment de **préserver les liquidités** et d'éviter les **risques d'obsolescence** du stock.
    A2) OBSF **maîtrise difficilement les délais** de ses produits en **"Fabless Manufacturing"**, les fournisseurs **s'impliquant souvent trop peu**. Ce mode de "production à distance" implique une synchronisation et une communication constante avec les fournisseurs.     

=====================================================
B) Traçabilité
=====================================================

    Les vélos et certains composants doivent être **identifiés et tracés spécifiquement par des Nos de série ou de lot**. Plusieurs raisons à cela, entre autre :

    - Service après-vente :
        - Livrer la bonne pièce de remplacement, ou une alternative compatible.
        - Offrir les prestations sous garantie uniquement lorsque celle-ci s'applique et éviter la fraude. 
        - Evaluer le taux de respect des spécifications techniques par les fournisseurs, par la remontée statistique des problèmes.

    - Rappel de produits non conformes
        - Etre en mesure d'informer et de rappeler les produits, en cas de découverte de produits non conformes, ou présentant un risques de sécurité pour l'utilisateur.

    - Contrôle des circuits de distribution
        - Etre en mesure d'identifier les revendeurs qui vendraient hors du territoire qui leur a été attribué.

    B1) Le système doit permettre de connaître la **localisation d'un article** sérialisé **en tout temps**, depuis sa **première réception** chez OBSF jusqu'à la **livraison au client**, y compris à l'intérieur des stocks, des ateliers, et en transit. Ceci est bien sûr également valable si l'article a été intégré dans un groupe ou transformé.

    B2) Les employés des ateliers de montage souhaitent que leurs écrans de saisie soient **les plus conviviaux possible**, et qu'en cas d'erreur de saisie ou de composant, la **procédure de correction soit simple, rapide et intuitive**. Ceci évitera que des données erronnées soient saisies dans la précipitation, et par conséquent la perte de la trace des composants.  

=====================================================
C) Usabilité du MPS
=====================================================

    Les ventes des produits OBSF se réalisent durant toute l'année, mais **fluctuent fortement**
        - à certaines **périodes** et
        - selon les **régions**.

    Ainsi, les ventes de vélos sont 
        - très fortes au printemps, 
        - connaissent un pic avant les vacances d'été, puis
        - s'affaiblissent durant l'automne et l'hiver.
        
        Les ventes en Italie connaissent toutefois un pic de vente durant les fêtes de Noël.

    Le **service après-vente** a également identifié **des pics de demande de pièces de rechange et de consommables au printemps** et dans une moindre mesure en automne. Ceci s'explique par le fait que les clients révisent leurs vélos en prévision des vacances, ou réparent après les vacances.

    OBSF souhaite un outil pour gérer proprement ses prévisions de vente :
    
        - éviter de perdre des ventes du fait de rupture de stock (vélos et composants SAV)
        - éviter l'insatisfaction des clients du fait du manque de composants (SAV)
        - éviter les conflits entre les différents départements de vente de vélo et le SAV en cas de stocks insuffisants ou
        - faire appel à la responsabilité de chacun en cas de stocks trop importants, en conservant les prévisions de chacun
        - mise à disposition d'écrans de contrôle et d'alerte, voire capable de proposer des solutions.

    C1) OBSF a entendu parler du **module MPS d'Odoo Enterprise V11** et souhaiterait savoir dans quelle mesure il permettrait de se passer d'Excel pour couvrir les besoins précités,
    C2) Et comment ce système MPS réagit en cas de

        - déviation de la prévision,
        - de retard de production, ou
        - d'imprévus.


.. note::
   Les produits OBSF s'adressent à des clients connaisseurs. Certains sont prêts à attendre quelques semaines pour recevoir leur nouveau vélo.
   
   OBSF a toutefois remarqué que lorsque un modèle n'est pas livrable du stock, les **ventes chutent** de près de 30%. Il est donc crucial pour OBSF d'analyser constamment les tendances du marché et de **faire des prévisions de vente** proche de la réalité. Ceci a pour conséquence l'achat anticipé de composants et le stockage de produits finis.

   Le **SAV** requiert également des stock de pièces détachées. En effet, lorsque un article de réparation n'est pas disponible, les clients se fâchent souvent car ils ne peuvent pas disposer de leur vélo durant le délai de livraison.

   Les **financiers** ne cessent de rappeler que le stock coûte cher ! Ceci est correct si l'on considère que le coût du stock est évalué à 15% (infrastructure, manutention, perte, obsolescence, assurances, etc). D'autre part, le cash flow peut souffrir rapidement d'un stock trop important, sachant que OBSF emprunte à 4%.

   Nous avons donc ici un dilemne à traiter :
   -    Pas de stock : moins de ventes et un risque sur l'image de marque
   -    Trop de stock : risque financier, augmentation du prix des produits. 

   Nous ne nous intéresserons pas en totalité des calculs financiers liés aux stratégies de stockage, ce n'est pas le but direct de ce travail. Toutefois, afin de pouvoir trouver un point optimum entre la maximisation des ventes (et du bénéfice) et la minimisation du blocage des ressources de l'entreprise, notamment financières, il est important de distinguer :
   
   - les différents enjeux du stock :

        * cyclique : correspond au cycle "quantité demandée" * "temps de réappro"
        * sécurité : couvre les retards de livraison des fournisseurs ou une demande temporaire trop forte 
        * protégé  : nécessite une autorisation élevée afin d'être livré. Dans le cas d'une rupture de stock importante, on conservera un quantité minimale à la disposition exclusive des demandes les plus pressantes.
        * de synchronisation : lors de l'assemblage d'un groupe, il peut arriver qu'un composant soit en retard. Le stock des autres composants "à l'heure" forment le stock de synchronisation. 
        * spéculatif : acheter plus que strictement nécessaire, afin de bénéficier d'un avantage financier ou stratégique (profiter d'un cours de change favorable, d'un rabais spécial, etc.)
        * anticipé : produire de manière anticipée afin de lisser la charge de l'entreprise (fabriquer des skis également en été afin d'être prêt à livrer dès le début de l'hiver)
        * obsolète : produit en fin de vie, peu de chance d'être vendu
        * WIP : (Work-In-Progress / Work-In-Process) : stocks qui sont actuellement dans le processus de fabrication

   - les différentes typologies du stock

        * achetés/catalogue : articles du marché, revendu sans transformation par l'entreprise.
        * soutraité :  article fabriqué par un tiers, sur la base de spécifications de l'entreprise.
        * matières premières : articles achetés auprès de fournisseurs, dans le but de les transformés ultérieurement.
        * semi-finis : produits en cours de fabrication, non-vendables en l'état
        * finis : produits destinés à la vente.
        * emballage : destiné à l'emballage des marchandises en prévision de leur transport.

   On notera que OBSF reçoit des demandes de clients par deux canaux distinct :

   - des commandes de vélos finis.
       - planifiable (prévisions des vente, stratégie de pénétration)
       - fluctue en fonction des saisons
   - des commandes de pièces détachées.
       - rupture de stock a un fort impact négatif sur la renommée de la marque
       - partiellement planifiable (consommation passées, estimation du niveau d'usure du parc de vélos en clientèle, alerte sur faiblesse identifiée, etc.)



        
=====================================================
Les scénarios de test
=====================================================

A1 - MTS : Approvisionnement "Juste à temps" MTS
================================================

Objectifs du test
-------------------
        
    - Vérifier que le système achète et fabrique au plus tard en fonction des conditions suivantes :

        - Aucun stock
        - Article en gestion MTS
        - Régles de réapprovisionnement à zéro (Min : 0 / Max : 0 / Multiple : 1 / 0 days to purchase)
        - Pas de délai commercial standard (délai indicatif pour le client)

    - Vérifier globalement la mécanique d'achat / fabrication.
    
Conditions de test
------------------

        - Odoo Enterprise Version Odoo 11.0+e
        - Modules installés

            - Inventory
            - Manufacturing
            - Sales
            - Purchase Management

        - Paramètres activés

            - Sales/Delivery Date : Activé, de manière a pouvoir placer une ligne de commande à la date souhaitée
            - Inventory/Reservation : pas modifié, pour info sur Immediately after sales order confirmation
            - Inventory/Traceability

                - Lots & Serial Number : Activé
                - Expiration Dates : Non
                - Consignment : Non

            - Inventory/Warehouse

                - Storage Locations : Activé, pour que le scénario soit réaliste
                - Multi-warehouses : Non
                - Multi-step Routes : Non

            - Inventory/Advanced Scheduling

                - Security Lead Time for Sales : Non
                - No Rescheduling Propagation : Non

            - Manufacturing :

                - Work Orders & Quality : Activé

            - Purchases :

                - Invoicing/Bill Control : Delivered quantities
                - Products/Vendor Pricelists : Activé (pour pouvoir importer les informations des fournisseurs)
                - Dropshipping : Activé

        - Données de base selon fichiers ci-dessous :

            - :download:`Produits avec routes MTS (product_template) <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0100_product_template_V01.csv>`
            - :download:`Partenaires (res_partner) <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0200_res_partner_V01.csv>`
            - :download:`Infos Fournisseurs <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0300_supplier_info_V01.csv>`
            - :download:`Centres de travail <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0400_workcenters_V01.csv>`
            - :download:`Gammes opératoires <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0500_routings_V01.csv>`
            - :download:`Nomenclatures <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0600_boms_V01.csv>`
            - :download:`Points de commande <./test_files/dst-td-raw05-test/obsf_test_data_odoo11_0700_reorderpoints_V01.csv>`

        - Remarque : pas de stocks !


Conditions de réussite
----------------------
        
        - L'ordonnancement du produit commandé est réalisé par un calcul amont des délais cumulés de **fabrication / assemblage** ou **achat** en fonction de la date requise par le client et des stocks disponibles (en l'occurrence pas de stocks !).
        - Si la date requise par le client est trop courte, un ordonnancement aval est réalisé et une date réaliste de livraison est calculée.
        - Les délais des approvisionnements sont positionnés en fonction des dates des besoins qui les concernent (date du début de l'opération de l'ordre de fabrication MO).
        - Les quantités à approvisionner sont correctes (qté en besoin, min. qté minimale d'achat)


Procédure de test
-----------------

        - Base de données : dst-td-scenario_a1_v01-test
        - Enregistrement d'une commande de vente pour 1x vélo de montagne rouge AB1 (ref. FINI-0001) pour livraison dans 102 jours calendaires.

            - Date de commande : 13.07.2018
            - Date de livraison requise : 23.10.2018 (+102 jours)

        - INFO : Odoo identifie que le stock de vélos est à 0 et informe l'utilisateur
        - INFO : Une livraison est générée à la date le livraision requise
        - ACTION : Run Scheduler ("When you run the schedulers, Odoo tries to reserve the available stock to fulfill the existing pickings and verify if some reordering rules should be triggered.")
        - INFO : Un Ordre de Fabrication a été généré pour le vélo, début planifié dans -10 jours !


Résultats
---------

        - :download:`Fichier de résultats <./test_results/Resultats_Test_A1.xlsx>`

        - [OK] La date de livraison déterminée par le système est correcte, étant entendu que la date de livraison requise par le client (+102 jours) était supérieure au délai de production du vélo sans stocks (chemin critique de 93 jours).
        - [KO] L'ordre de fabrication principal (pour le vélo FINI-0001) a été positionné dans le passé à -10 jours, au lieu de +102 jours.
        - [KO] Le scheduler ne traite que le premier niveau de besoin. Dans le cas de notre vélo, il faut relancer le scheduler 5 fois afin de générer l'ensemble des MO et PO.
        - [KO] Tous les besoins sont planifiés dans le passé, alors qu'ils pourraient être positionnés au plus tard, en fonction de la hiérarchie des besoins.
        - [OK] Les quantités en besoin sont correctes.


Faiblesses identifiées
----------------------

        - Si un besoin est posé pour un article MTS qui n'a pas de Règle de réapprovisionnement, il semblerait que ce besoin soit ignoré par le scheduler, sans aucune information à l'utilisateur. Il est bien entendu possible de générer un ordre d'approvisionnement manuellement, mais le risque est important que le besoin soit perdu de vue et provoque des perturbations dans l'ordonnancement.
        - Le scheduler doit "tourner" plusieurs fois avant que l'ensemble des ruptures de stock ne soient identifiées. Ceci a pour conséquence que si le scheduler est exécuté automatiquement toutes les 24 heures, les composants de dernier niveau de notre vélo ne seront commandés que 4 jours plus tard.


Commentaire
-----------

        - Le mode de gestion Make-To-Stock MTS d'Odoo est dédié au réapprovisionnement du stock "au plus tôt". Ce n'est pas un besoin à une date qui réclame du stock, c'est une quantité insuffisante dans le stock. Il ne prend pas en considération la date du besoin. 
        - Fort de ce constat, je décide d'évaluer le système Make-To-Order MTO afin de vérifier s'il correspond mieux au besoin de produire au plus tard. 


A1 - MTO : Approvisionnement "Juste à temps" MTO
================================================

Objectifs du test
-----------------

        - Vérifier que le système achète et fabrique au plus tard en fonction des conditions suivantes :

            - Aucun stock
            - Article en gestion MTO
            - Régles de réapprovisionnement à zéro (Min : 0 / Max : 0 / Multiple : 1 / 0 days to purchase)
            - Pas de délai commercial standard (délai indicatif pour le client)

        - Vérifier globalement la mécanique d'achat / fabrication.
    
Conditions de test
------------------

        - Système identiques au test A1 - MTS, sauf

            - Tous les articles en MTO

                .. figure:: ../img/product_route_mto.png
                   :scale: 70%
                   :alt: product_route_mto
                   :align: center

                - :download:`Produits avec routes MTO <./test_files/A1_MTO/product_template_mto.csv>`


Conditions de réussite
----------------------
        
        - L'ordonnancement du produit commandé est réalisé par un calcul amont des délais cumulés de **fabrication / assemblage** ou **achat** en fonction de la date requise par le client et des stocks disponibles (en l'occurrence pas de stocks !).
        - Si la date requise par le client est trop courte, un ordonnancement aval est réalisé et une date réaliste de livraison est calculée.
        - Les délais des approvisionnements sont positionnés en fonction des dates des besoins qui les concernent (date du début de l'opération de l'ordre de fabrication MO).
        - Les quantités à approvisionner sont correctes (qté en besoin, min. qté minimale d'achat)


Procédure de test
-----------------

        - Base de données : dst-td-scenario_a1_v02-test
        - Enregistrement d'une commande de vente pour 1x vélo de montagne rouge AB1 (ref. FINI-0001) pour livraison dans 102 jours calendaires.

            - Date de commande : 30.07.2018
            - Date de livraison requise : 10.11.2018 (+102 jours)

        - INFO : Une livraison est générée à la date le livraision requise
        - ACTION : Run Scheduler ("When you run the schedulers, Odoo tries to reserve the available stock to fulfill the existing pickings and verify if some reordering rules should be triggered.")
        - INFO : Un Ordre de Fabrication a été généré pour le vélo, début planifié dans -10 jours !


Résultats
---------

        :download:`Fichier de résultats <./test_results/Resultats_Test_A1_MTO.xlsx>`

        - [OK] La date de livraison déterminée par le système est correcte, étant entendu que la date de livraison requise par le client (+102 jours) était supérieure au délai de production du vélo sans stocks (chemin critique de 93 jours).
        - [OK] L'ensemble des MO et PO ont été générés, sans nécessité de faire tourner le scheduler.
        - [OK] Les quantités en besoin sont correctes.
        - [KO] La plupart des besoins ont été placés correctement dans le temps. Toutefois, la date d'achat de l'article RAW-0301 a été posée à 0 jours de la date planifiée, alors que la fiche fournisseur indique 40 jours. La raison était que la fiche fournisseur prévoyait une quantité minimale d'achat de 100 pces, alors que le besoin MTO n'était que d'une pièce. Une deuxième fiche avec quantité minimale à 1 a résolu le problème du délai.
        - [A vérifier] Pour la commande PO000001, le système à regroupé 3 besoins sous un RFQ au même fournisseur, alors que leurs dates de besoin sont différentes. Quelles sont les règles de regroupement ?

        
Faiblesses identifiées
----------------------

        - `[A1_MTO_F01] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ Dans le cas où la seule fiche fournisseur indique une quantité minimale d'achat supérieure au besoin MTO, le système détermine correctement le fournisseur, mais pas le délai, ni le prix. Ceci a pour conséquence que l'achat pourrait être tardif et engendrer un retard de livraison.
        - `[A1_MTO_F02] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ Lors du test, une erreur de manipulation m'a contraint à supprimer la commande de vente. De manière surprenante, les MO et PO y relatifs n'ont pas été supprimés.
        - `[A1_MTO_F03] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ La suppression d'une commande de vente pour article MTO ne réactualise pas le forecast de l'article.
        - En cas de suppression d'un PO pour un article MTO, le système ne le régénèra que si l'article dispose d'une règle de réapprovisionnement et en faisant tourner le scheduler. Le besoin se placera alors selon les règles MTS, soit "au plus tôt"
        - Le système génère les RFQ sans tenir compte des quantités économiques (paliers de prix des infos fournisseurs).
        - Le système réordonne les Infos Fournisseurs à la sauvegarde du produit. Quelles sont ces règles et l'impact ? 

        .. figure:: ../img/Odoo_Change_Ordre_FIA.gif
            :scale: 60%
            :alt: Odoo_Change_Ordre_FIA
            :align: center 

Commentaire
-----------
            - Le mode de gestion Make-To-Order MTO d'Odoo est dédié au réapprovisionnement des besoins stricts. Il ne prend pas en considération les données d'une fiche fournisseur existante. 


A1 - MTO-MTS_V01 : Test du module OCA mrp_mto_with_stock
=========================================================================

Objectifs du test
-----------------

        - Vérifier que le système achète et fabrique au plus tard en fonction des conditions suivantes :

            - Aucun stock
            - Article en gestion MTO-MTS
            - Régles de réapprovisionnement à zéro (Min : 0 / Max : 0 / Multiple : 1 / 0 days to purchase)
            - Pas de délai commercial standard (délai indicatif pour le client)

        - Vérifier globalement la mécanique d'achat / fabrication.
    
Conditions de test
------------------

        - Système identiques au test A1 - MTS, sauf

            - Module `OCA mrp_mto_with_stock <https://github.com/OCA/manufacture/tree/11.0/mrp_mto_with_stock>`_ installé

            - Tous les articles en MTO_MTS

                .. figure:: ../img/product_route_mto.png
                   :scale: 70%
                   :alt: product_route_mto
                   :align: center

                - :download:`Produits avec routes MTO <./test_files/A1_MTO/product_template_mto.csv>`


Conditions de réussite
----------------------
        
        - L'ordonnancement du produit commandé est réalisé par un calcul amont des délais cumulés de **fabrication / assemblage** ou **achat** en fonction de la date requise par le client et des stocks disponibles (en l'occurrence pas de stocks !).
        - Si la date requise par le client est trop courte, un ordonnancement aval est réalisé et une date réaliste de livraison est calculée.
        - Les délais des approvisionnements sont positionnés en fonction des dates des besoins qui les concernent (date du début de l'opération de l'ordre de fabrication MO).
        - Les quantités à approvisionner sont correctes (qté en besoin, min. qté minimale d'achat)


Procédure de test
-----------------

        - Base de données : dst-td-scenario_a1_v02-test
        - Enregistrement d'une commande de vente pour 1x vélo de montagne rouge AB1 (ref. FINI-0001) pour livraison dans 102 jours calendaires.

            - Date de commande : 30.07.2018
            - Date de livraison requise : 10.11.2018 (+102 jours)

        - INFO : Une livraison est générée à la date le livraision requise
        - ACTION : Run Scheduler ("When you run the schedulers, Odoo tries to reserve the available stock to fulfill the existing pickings and verify if some reordering rules should be triggered.")
        - INFO : Un Ordre de Fabrication a été généré pour le vélo, début planifié dans -10 jours !


Résultats
---------

        :download:`Fichier de résultats <./test_results/Resultats_Test_A1_MTO.xlsx>`

        - [OK] La date de livraison déterminée par le système est correcte, étant entendu que la date de livraison requise par le client (+102 jours) était supérieure au délai de production du vélo sans stocks (chemin critique de 93 jours).
        - [OK] L'ensemble des MO et PO ont été générés, sans nécessité de faire tourner le scheduler.
        - [KO] La plupart des besoins ont été placés correctement dans le temps. Toutefois, la date d'achat de l'article RAW-0301 a été posée à 0 jours de la date planifiée, alors que la fiche fournisseur indique 40 jours. La raison était que la fiche fournisseur prévoyait une quantité minimale d'achat de 100 pces, alors que le besoin MTO n'était que d'une pièce. Une deuxième fiche avec quantité minimale à 1 a résolu le problème du délai.
        - [A vérifier] Pour la commande PO000001, le système à regroupé 3 besoins sous un RFQ au même fournisseur, alors que leurs dates de besoin sont différentes. Quelles sont les règles de regroupement ?
        - [OK] Les quantités en besoin sont correctes.

        
Faiblesses identifiées
----------------------

        - `[A1_MTO_F01] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ Dans le cas où la seule fiche fournisseur indique une quantité minimale d'achat supérieure au besoin MTO, le système détermine correctement le fournisseur, mais pas le délai, ni le prix. Ceci a pour conséquence que l'achat pourrait être tardif et engendrer un retard de livraison.
        - `[A1_MTO_F02] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ Lors du test, une erreur de manipulation m'a contraint à supprimer la commande de vente. De manière surprenante, les MO et PO y relatifs n'ont pas été supprimés.
        - `[A1_MTO_F03] <https://nextcloud.open-net.ch/index.php/s/HaqniNCeQogjq36>`_ La suppression d'une commande de vente pour article MTO ne réactualise pas le forecast de l'article.
        - En cas de suppression d'un PO pour un article MTO, le système ne le régénèra que si l'article dispose d'une règle de réapprovisionnement et en faisant tourner le scheduler. Le besoin se placera alors selon les règles MTS, soit "au plus tôt"
        - Le système génère les RFQ sans tenir compte des quantités économiques (paliers de prix des infos fournisseurs).
        - Le système réordonne les Infos Fournisseurs à la sauvegarde du produit. Quelles sont ces règles et l'impact ? 

        .. figure:: ../img/Odoo_Change_Ordre_FIA.gif
            :scale: 60%
            :alt: Odoo_Change_Ordre_FIA
            :align: center 

Commentaire
-----------
            - Le mode de gestion Make-To-Order MTO d'Odoo est dédié au réapprovisionnement des besoins stricts. Il ne prend pas en considération les données d'une fiche fournisseur existante. 

