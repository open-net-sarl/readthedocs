##############################################################
Résultats de l'étude
##############################################################

==============================================================
Faiblesses identifiées
==============================================================

Afin de pouvoir évaluer et qualifier l'importance des faiblesses identifiées durant les tests, j'ai décidé de dessiner un flux transversal client - fournisseur, que j'ai **arbitrairement** considéré comme standard.

Ceci m'a permis de placer sur ce schéma les points faibles identifiés, de les qualifier et de comparer ma compréhension de la criticité du point avec celle de mon mandant.

Voici cette carte, que nous appellerons "Situation AS-IS" (telle quelle), puisque c'est l'état constaté du système actuel. Chaque triangle rouge identifie une faiblesse constatée et précises l'élément du flux qu'elle impacte.

    .. figure:: ../img/Odoo11_Process_AS-IS.png
        :alt: Situation as-is
        :align: center

    :download:`Situation AS-IS (pdf) <./media/Odoo11_Process_AS-IS.pdf>` :download:`(svg) <./media/Odoo11_Process_AS-IS.svg>`


:X01 - Annulation de commande de vente MTO: En cas d'annulation d'un poste de commande de vente pour un article MTO, les ordres d'approvisionnement non confirmés ne sont pas supprimés (alors que c'était le cas en V10).
    
    N.B. Il s'agit probablement d'un paramètrage manquant en version 11 standard, facilement réactivable.  
:S01 - Détermination du délai de livraison: S'il y a du stock disponible, le délai est immédiat. Dans le cas contraire, il correspond au délai standard de produit. Le système ne considère pas les entrées planifiées entre ces deux échéances.
:X02 - Règle de réapprovisionnement: Si le produit à un emplacement déterminé n'a pas de règle de réapprovisionnement, le système ne déclenche ni approvisionnement, ni avertissement en cas de besoin.
:M01 - Planification: Le système génère des RFQ ou MO dans le passé lorsque le délai ne peut plus être tenu (MTS, MTO et MPS-Make).  Mais pas en MPS-Buy !
:B01 - Sélection du fournisseur: Le système prend systématiquement le premier fournisseur de la fiche produit, même si les conditions ne s'appliquent pas !

    N.B. Ce fonctionnement est probablement souhaité par l'éditeur, afin de permettre au client de déterminer sa propre séquence de sélection du meilleur fournisseur. Mais un filtre portant notamment sur les dates de validité serait probablement judicieux.
:B02 - Planification: Le système n'informe / ne corrige pas les éléments dépendants en cas de nouveau délai.

========================================================
Modules complémentaires à étudier
========================================================

`OCA - Odoo Community Association <https://odoo-community.org>`_
==================================================================

-   `manufacture <https://github.com/OCA/manufacture>`_
-   `manufacture-reporting <https://github.com/OCA/manufacture-reporting>`_
-   `purchase-workflow <https://github.com/OCA/purchase-workflow>`_
-   `stock-logistics-warehouse <https://github.com/OCA/stock-logistics-warehouse>`_
-   `stock-logistics-transport <https://github.com/OCA/stock-logistics-transport>`_


`Odoomrp.com <http://www.odoomrp.com>`_
=====================================================

-   `odoomrp-utils <https://github.com/odoomrp/odoomrp-utils>`_
-   `odoomrp-wip <https://github.com/odoomrp/odoomrp-wip>`_

================================================================
Décisions
================================================================

Après discussion avec le mandant, nous décidons de résoudre prioritairement le point S01, car :

    - On sait que les clients sont habitués à être livré rapidement. Lors d'une demande client, si un produit n'est pas livrable du stock, la probabilité que le client n'achète pas augmente proportionnellement au délai d'attente. Offir à ce moment un délai standard, c'est mieux que rien, mais si du stock pourrait être disponible entre ces deux dates, autant en profiter et maximiser les chances de transformation en commande ferme.  

    - La solution au point S01 signifie l'ajout d'une possibilité de **questionner l'arbre des encours d'approvisionnement** et des stocks intermédiaires,  afin d'obtenir un délai plausible.

    - Cette solution présuppose que les éléments d'approvisionnement sont placés judicieusement dans le temps. Or, les faiblesses constatées M01 et B02 précisent justement que le système est en difficulté dans ce domaine.

    - Nous allons donc également au préalable résoudre les points M01 et B02, par un **module de recalcul des dates des éléments d'approvisionnement en cours**. 
