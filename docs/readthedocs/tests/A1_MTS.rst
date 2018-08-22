================================================
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

            - :download:`Produits avec routes MTS (product_template) <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0100_product_template_V01.csv>`
            - :download:`Partenaires (res_partner) <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0200_res_partner_V01.csv>`
            - :download:`Infos Fournisseurs <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0300_supplier_info_V01.csv>`
            - :download:`Centres de travail <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0400_workcenters_V01.csv>`
            - :download:`Gammes opératoires <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0500_routings_V01.csv>`
            - :download:`Nomenclatures <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0600_boms_V01.csv>`
            - :download:`Points de commande <../test_files/dst-td-raw05-test/obsf_test_data_odoo11_0700_reorderpoints_V01.csv>`

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

        - :download:`Fichier de résultats <../test_results/Resultats_Test_A1.xlsx>`

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
