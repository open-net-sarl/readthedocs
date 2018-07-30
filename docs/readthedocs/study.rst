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
        
=====================================================
Les scénarios de test
=====================================================

A1) Approvisionnement "Juste à temps"

    - Objectifs du test
        
        - Vérifier que le système achète et fabrique au plus tard en fonction des conditions suivantes :

            - Aucun stock
            - Régles de réapprovisionnement à zéro (Min : 0 / Max : 0 / Multiple : 1 / 0 days to purchase)
            - Pas de délai commercial standard

        - Vérifier globalement la mécanique d'achat / fabrication.

    - Conditions de réussite
        
        - L'ordonnancement du produit commandé est réalisé par un calcul amont des délais cumulés de **fabrication / assemblage** ou **achat** en fonction de la date requise par le client et des stocks disponibles (en l'occurrence pas de stocks !).
        - Si la date requise par le client est trop courte, un ordonnancement aval est réalisé et une date réaliste de livraison est calculée.
        - Les délais des approvisionnements sont positionnés en fonction des dates des besoins qui les concernent (date du début de l'opération de l'ordre de fabrication MO).

        - Les approvisionnements sont orientés sur le "bon fournisseur" (fiche info-fournisseur en cours de validité)
        - Les quantités à approvisionner sont correctes (qté en besoin, min. qté minimale d'achat)
        - Les prix d'achat sont corrects
    
    - Conditions de test

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

        - Données de base selon fichiers

            - obsf_test_data_odoo11_0100_product_template_V01.csv
            - obsf_test_data_odoo11_0200_res_partner_V01.csv
            - obsf_test_data_odoo11_0300_supplier_info_V01.csv
            - obsf_test_data_odoo11_0400_workcenters_V01.csv
            - obsf_test_data_odoo11_0500_routings_V01.csv
            - obsf_test_data_odoo11_0600_boms_V01.csv
            - obsf_test_data_odoo11_0700_reorderpoints_V01.csv

            `local mirror <test_files/obsf_test_data_odoo11_0700_reorderpoints_V01.csv>`_

            - pas de stocks


    Procédure de test

    - Enregistrement d'une commande de vente pour 1x vélo de montagne rouge AB1 (ref. FINI-0001) pour livraison dans 102 jours calendaires.

        - Date de commande : 13.07.2018
        - Date de livraison requise : 23.10.2018


    Faiblesses identifiées

    - Si un article ne possède pas de Règle de réapprovisionnement, il semblerait que le besoin d'une commande soit perdu.

        - A vérifier et éventuellement adapter le code.
        - Il est nécessaire de faire tourner le scheduler autant de fois que le nombre de niveaux de la nomenclature du produit vendu. 