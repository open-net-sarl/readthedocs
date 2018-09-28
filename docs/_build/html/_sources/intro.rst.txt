########################
Introduction
########################

===========================================
Cadre de l'étude
===========================================

Cette documentation est établie dans le cadre de mon travail de diplôme de `l'Ecole Supérieure d'Informatique de Gestion <http://www.esig-jura.ch>`_ de `Delémont <https://en.wikipedia.org/wiki/Delémont>`_.

Etudier le fonctionnement logistique d'un système ERP et proposer des solutions d'amélioration nécessite une expérience terrain importante, sachant que l'équivalent sur un corps humain reviendrait à étudier l'ensemble du système sanguin, probablement quelques mécanismes du système nerveux, voire le système limphatique.

Longtemps, on a par exemple soigné la fièvre par `des saignées <https://fr.wikipedia.org/wiki/Saignée_(médecine)>`_, jusqu'au jour où on s'est aperçu que la situation du malade se dégradait plus qu'elle ne s'améliorait.


    .. figure:: ./img/Pratique_d'une_saignée.jpg
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
La fabrication
======================================================

========================
Licence
========================

.. raw:: html
   :file: licence.html