
###############################
Etude et tests
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

    C1) OBSF a entendu parler du `module MPS d'Odoo Enterprise V11 <https://www.odoo.com/slides/slide/mrp-ii-scheduler-and-master-production-schedule-422>`_ et souhaiterait savoir dans quelle mesure il permettrait de se passer d'Excel pour couvrir les besoins précités,
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

   On relevera que OBSF reçoit les demandes de clients par deux canaux distinct :

   - des commandes de vélos finis.
       - planifiable (prévisions des vente, stratégie de pénétration)
       - fluctue en fonction des saisons
   - des commandes de pièces détachées.
       - rupture de stock a un fort impact négatif sur la renommée de la marque
       - partiellement planifiable (consommation passées, estimation du niveau d'usure du parc de vélos en clientèle, alerte sur faiblesse identifiée, etc.)



        
=====================================================
Les scénarios de test
=====================================================

.. toctree::
    :maxdepth: 5
    :numbered:
    :glob:

    tests/A1_MTS
    tests/A1_MTO
    tests/A1_MTO_MTS
    tests/C1_MPS