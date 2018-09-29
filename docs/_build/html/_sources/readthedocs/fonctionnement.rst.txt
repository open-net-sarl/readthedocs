################################################
Le fonctionnement logistique du système Odoo V11
################################################

=====================================================
Le processus standard
=====================================================

Le processus intégré depuis la vente
------------------------------------

    .. figure:: ../img/processus_commercial_standard01.png
        :alt: Processus logistique et commercial standard
        :scale: 70%
        :align: center

    :download:`Processus logistique et commercial standard (pdf) <./media/Odoo11_Process_AS-IS.pdf>`

Démonstration
-----------------

    :download:`Démonstration "Enregistrement d'une commande pour un vélo" <./media/odooV11e_demo_velos_mto_v01.pdf>`


=====================================================
La structure logistique
=====================================================

Ce schéma décrit les emplacements de stock de stocks standards du système Odoo de base, avec leurs parents respectifs (Société, Entrepôt, Emplacement parent). Les routes entre ces emplacements sont également spécifiées.

    .. figure:: ../img/routes_et_emplacements01_map_paysage.png
        :alt: Routes et Emplacements de stock
        :align: center

    :download:`Routes et Emplacements de stock (pdf) <./media/Odoo11_Routes_et_Emplacements_de_stock_V02.pdf>`

    :download:`Routes et Emplacements de stock (svg) <./media/Odoo11_Routes_et_Emplacements_de_stock_V02.svg>`

=========================  =============================================================================
Type d'emplacement         Description
Emplacement fournisseur    Un emplacement virtuel qui correspond à l'emplacement d'origine 
                           des produits issus de vos fournisseurs. 
Vue                        Emplacement virtuel utilisé pour créer des structures hiérarchiques pour votre entrepôt, en agrégeant
                           ses emplacements enfants ; ne peut pas directement contenir de produits.
Emplacement interne        L'emplacement physique dans votre entrepôt.
Emplacement client         Un emplacement virtuel qui correspond à l'emplacement de destination des produits envoyés à vos clients.
Perte de stock             Emplacement virtuel servant de contre-valeur aux opérations d'inventaire utilisées pour corriger les niveaux de stock                                        (inventaires physiques).
Approvisionnement          Emplacement virtuel servant de contre-valeur temporaire pour les opérations d'approvisionnement lorsque la source
                           (fournisseur ou fabrication) n'est pas encore connue. Normalement, cet emplacement est vide une fois que le
                           planificateur d'approvisionnement a fini de s'exécuter.
Fabrication                Emplacement virtuel de contre-valeur pour les opérations de fabrication.
                           Cet emplacement consomme des matières premières et fabrique des produits finis.
Emplacement de transit     emplacement physique de contre-valeur à utiliser pour les opérations inter-entreprises et inter-entrepôts.
=========================  =============================================================================

Les entrepôts
-------------------------

Les emplacements de stock
-------------------------

=====================================================
Les flux internes et externes
=====================================================

    .. figure:: ../img/routes_et_qualite01.png
        :scale: 70%
        :alt: Routes et Qualite
        :align: center

    :download:`Routes et Qualité (pdf) <./media/Odoo11_Qualite_et_routes_V01.pdf>`

Les routes
-------------------------

Les règles
-------------------------

