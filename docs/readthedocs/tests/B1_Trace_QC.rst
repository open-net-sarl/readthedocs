================================================
B1 : Quality Control
================================================

Objectifs du test
-------------------
        
    - Vérifier que le système enregistre correctement les Nos de série et Nos de lots durant tout le processus logistique:

        - Articles sérialisés

    - Vérifier globalement la succession logique des écrans de saisie.
    
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


Conditions de réussite
----------------------
        
        - Tous les mouvements de stock réalisés sur des éléments sérialisés sont répertoriés
        - Une arborescence démontrant la trace d'un produit sérialisé permet de retrouver l'ensemble des documents parcouru par un article sérialisé, depuis le fournisseur au client.


Procédure de test
-----------------

        - Base de données : dst-td-raw05-test


Résultats
---------

        `Vidéo de démonstration du flux <https://nextcloud.open-net.ch/index.php/s/HYtXQgAbbLfz3pw>`_

        .. figure:: ../../img/traceability01.png
            :alt: Rapport de traçabilité
            :align: center

        :download:`Rapport de traçabilité (pdf) <../media/Rapport_de_Tracabilite.pdf>`

        - [OK] Les nos de série sont réclamés et enregistrés à chaque mouvement de stock.
        - [OK] La séquence des écrans de saisie dans les ordres de travail est correcte.
        - [KO] Le rapport n'est pas éclaté correctement.


Faiblesses identifiées
----------------------

        - Le rapport qui ne s'éclate pas correctement (n'éclate qu'un niveau apparemment)

Commentaire
-----------

        - Le mandant connait déjà le problème sur l'éclatement du rapport. Ce phénomène est corrigé par un fix en attendant que l'éditeur ne corrige ce qui semble être un bug.
