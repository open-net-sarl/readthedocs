###############################
Maintenance de la documentation
###############################

=====================================================
Fonctionnement de la chaîne d'édition 
=====================================================

   .. figure:: ../img/rtd_logo_sm.jpg
      :scale: 70%
      :alt: logo ReadtheDocs
      :align: center
      :target: https://readthedocs.org     

.. note::
   Cette documentation est générée et hébergée par le site :term:`"Read the Docs"<Read the Docs>`, qui permet sa mise à jour **en continu**, avec notamment les caractéristiques suivantes:

   * un système de recherche intégré
   * une édition simplifiée
   * une mise en forme structurée et rigide (idéale pour des documents techniques)
   * une gestion de plusieurs versions
   * une édition en plusieurs langues

* Les fichiers sources sont stockés dans un répertoire de :term:`Github.com <github>`.
* Ils sont écrits en language :term:`reStructuredText <RST>` (extension .rst).
* Un :term:`webhook<webhook>` est établi entre :term:`"Read the Docs"<Read the Docs>` et les fichiers sources sous :term:`Github.com <github>`.
* A chaque changement d'un fichier source, le :term:`webhook<webhook>` active la régénéraion du site en ligne.

============
Prérequis
============

* Disposer d'une compte chez :term:`Github.com <github>` (ou similaire)
* Disposer d'un compte chez :term:`"Read the Docs"<Read the Docs>` connecté aux sources du compte :term:`Github.com <github>`.

Compléments
-----------
Afin d'assurer un meilleur confort d'édition, les logiciels ci-après peuvent être installés en complément :

* Un éditeur de code (:term:`Visual Studio Code` dans notre cas)
* Le moteur d'édition :term:`Sphinx <sphinx>`, qui est le moteur de génération de :term:`"Read the Docs"<Read the Docs>`.

==========================================
Mise en place d'une nouvelle documentation
==========================================

* Sous :term:`Github.com <github>`

  * Créer un repository sous :term:`Github.com <github>`
  * relever :abbr:`l'URL de celui-ci (par exemple : https://github.com/open-net-sarl/readthedocs.git)`.

* Sous Read the Docs

  * Cliquer **Import a Project** et sélectionner un Repository
  * Cliquer **Admin > Settings**. Vérifier l'URL du champ "Repository URL".
  * Adapter les autres champs en fonction du besoin, notamment l'édition au format PDF ou ePub, en plus de HTML
  * Cliquer **Admin > Settings > Advanced Settings**. Vérifier le niveau de confidentialité sous "Privacy Level".

  .. note::
     Cette installation minimale permet déjà de créer une documentation en ligne en éditant des fichier :abbr:`.rst (restructuredText)` directement sous :term:`Github.com <github>`.
     
     Ceci constitue toutefois une solution peu élégante. D'autre part, le résultat de la conversion des fichiers .rst vers html par :term:`"Read the Docs"<Read the Docs>` est assez lente.

     Afin de travailler dans de meilleures conditions, nous allons procéder en complément à l'installation d'un éditeur de code connecté à :term:`Github.com <github>`, ainsi qu'à l'installation du moteur de génération de documentation :term:`Sphinx <sphinx>` (qui est identique à celui de :term:`"Read the Docs"<Read the Docs>`).   

=============================================
Installation du système pour l'édition locale
=============================================

* Installation du moteur :term:`Sphinx <sphinx>`

  .. note::
     :term:`Sphinx <sphinx>` a besoin de Python pour fonctionner. Sous Windows, l'installation de :term:`Anaconda <anaconda>` constitue probablement l'option la plus simple.

  * Télécharger et installer :term:`Anaconda <anaconda>`
  * Ouvrir la console "Anaconda Prompt"

    .. code-block:: Python

        conda install sphinx    # Installation de Sphinx

    Pour générer un nouveau projet :

    .. code-block:: Python

        cd /path/to/project/
        mkdir docs
        cd docs
        sphinx-quickstart
        # Répondre aux questions en validant les valeurs proposée en cas de doute, il est possible de reconfigurer le projet ultérieurement.
        # Vous obtiendrez un fichier de configuration de base conf.py et
        # un document d'index basique, mais fonctionnel et prêt à être édité. 

    Pour générer le site html à partir des sources existantes :

    .. code-block:: Python

        # pour générer les documents en html :
        cd /path/to/project/docs
        make html
        # un dossier _build existe dorénavant, avec les fichiers sources du site html
        # vous pouvez consulter le site généré en local sous 'file:///path/to/project/docs/_build/html/index.html

    Optionnel : pour automatiser la régénération de la documentation html à chaque modification d'un fichier source :

    .. code-block:: Python

        # installer les modules nécessaires
        conda install -c conda-forge sphinx-autobuild
        # se déplacer dans le répertoire de la documentation
        cd /path/to/project/docs
        # initialiser la régénération automatique
        sphinx-autobuild . _build/html
        # Dès maintenant, la documentation est disponible en local à l'adresse http://localhost:8000.
        # il suffit de raffraîchir la page du navigateur (CTRL+F5) pour oubtenir la nouvelle version
        # après quelques secondes.
        #
        # interrompre cet automatisme avec CTRL+C


* Sous :term:`Visual Studio Code`

  * Installer le contrôle de code source git au besoin
  * Créer un répertoire pour les documents de projet en local
  * Initialiser le `répertoire pour git <https://www.youtube.com/watch?v=6n1G45kpU2o>`_.
  * Connecter le git local au `git distant <https://stackoverflow.com/a/43364619>`_

    .. code-block:: bash

        cd /home/myProject/
        git remote add origin https://...
        git remote show origin # if everything is ok, you will see your remote
        git push -u origin master # assuming your are on the master branch.

.. warning::
    Ne pas oublier de pousser les modifications régulièrement vers :term:`Github.com <github>`, sans quoi le site online ne sera pas mis à jour.

