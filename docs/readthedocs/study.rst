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
Approvisionnement "Juste-à-temps"
=====================================================

    #. Le système doit permettre de commander et d'être livré "au plus tard" ou **"juste-à-temps"**, c'est-à-dire au moment précis des besoins de l'ordonnancement. Ceci permet notamment de **préserver les liquidités** et d'éviter les **risques d'obsolescence** du stock.
    #. OBSF **maîtrise difficilement les délais** de ses produits en **"Fabless Manufacturing"**, les fournisseurs **s'impliquant souvent trop peu**. Ce mode de "production à distance" implique une synchronisation et une communication constante avec les fournisseurs.     

=====================================================
Traçabilité
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

    #. Le système doit permettre de connaître la **localisation d'un article** sérialisé **en tout temps**, depuis sa **première réception** chez OBSF jusqu'à la **livraison au client**, y compris à l'intérieur des stocks, des ateliers, et en transit. Ceci est bien sûr également valable si l'article a été intégré dans un groupe ou transformé.

    #. Les employés des ateliers de montage souhaitent que leurs écrans de saisie soient **les plus conviviaux possible**, et qu'en cas d'erreur de saisie ou de composant, la **procédure de correction soit simple, rapide et intuitive**. Ceci évitera que des données erronnées soient saisies dans la précipitation, et par conséquent la perte de la trace des composants.  

=====================================================
Usabilité du MPS
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

    #. OBSF a entendu parler du **module MPS d'Odoo Enterprise V11** et souhaiterait savoir dans quelle mesure il permettrait de se passer d'Excel pour couvrir les besoins précités,
    #. Et comment ce système MPS réagit en cas de

        - déviation de la prévision,
        - de retard de production, ou
        - d'imprévus.