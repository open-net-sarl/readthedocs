============================================================
C1 - MPS : Approvisionnement basé sur une prévision de vente
============================================================

Objectifs du test
-----------------

        - Vérifier que les faiblesses constatées lors les tests A1_MTO et A1_MTS sont corrigées par le module MPS
        - Vérifier globalement la mécanique du module MPS.
    
Conditions de test
------------------

        - Système identiques au test A1 - MTS, avec ajout des articles spécifiques suivants :

        .. figure:: ../../img/Produits_Tests_MPS.png
                :alt: Produits pour le test MPS
                :align: center

Conditions de réussite
----------------------
        
        - Les prévisions réalisables au délai souhaité sont validées
        - Les prévisions non réalisables au délai souhaité sont repoussées à un délai réalisables
        - L'utilisateur en est informé - par exemple par des codes de couleur
        - Lors ordres d'approvisionnement dans l'horizon du besoin sont générés 


Procédure de test
-----------------

        - Base de données : dst-td-mps-eval01-test


Résultats
---------

        `Vidéo du test MPS <https://nextcloud.open-net.ch/index.php/s/Qi5JayK3ARzG3cw>`_

        :download:`Vidéo du test MPS (MP4) <../test_results/MPS_01/MPS_Test01.mp4>`

        - [OK] Les prévisions sont enregistrées et transmises à la planification
        - [KO] La planification est effectuée avec les mêmes faiblesses que constatées lors les tests A1_MTO et A1_MTS


Faiblesses identifiées
----------------------

        - Identiques à A1_MTO et A1_MTS

Commentaire
-----------

        - Le module MPS nécessite que l'ensemble des articles à planifier soient enregistrés, y compris les composants. Ceci constitue un risque d'oubli, alors que seuls les articles de tête ne devraient être planifiés et les besoins de leurs composants cascadés.

        - Le module MPS génère des besoins prévisionnels. Il ne vérifie pas ultérieurement si cette prévision a été respectée.   

