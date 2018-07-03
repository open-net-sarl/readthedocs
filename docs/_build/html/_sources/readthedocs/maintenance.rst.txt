###############################
Maintenance de la documentation
###############################

=====================================================
Fonctionnement de la chaîne d'édition "Read the Docs"
=====================================================

.. note::
   Le système ReadtheDocs permet l'édition **en continu** d'une documentation **en ligne**, avec notamment :

   * un système de recherche intégré
   * une édition simplifiée
   * une mise en forme structurée et rigide (idéale pour des documents techniques)
   * une gestion de plusieurs version
   * multilangue

* Les fichiers sources sont stockés dans un répertoire de `Github.com <https://github.com>`_.
* Ils sont écrits en language reStructuredText (extension .rst)
* Un `webhook <https://en.wikipedia.org/wiki/Webhook>`_ est établi entre `Read the Docs <https://readthedocs.org>`_ et les fichiers sources sous Github.com.
* A chaque changement d'un fichier source, le webhook active la régénéraion du site en ligne.

============
Prérequis
============

* Disposer d'une compte chez `Github.com <https://github.com>`_ (ou similaire)
* Disposer d'un compte chez `Read the Docs <https://readthedocs.org>`_ connecté aux sources du compte Github.

Compléments
-----------
Afin d'assurer un meilleur confort d'édition, les logiciels ci-après peuvent être installés en complément :

* Un éditeur de code (`Visual Studio Code <https://code.visualstudio.com/>`_ dans notre cas)
* Le moteur d'édition `Sphinx <http://www.sphinx-doc.org/en/master/>`_, qui est le moteur de génération de ReadTheDocs.

==========================================
Mise en place d'une nouvelle documentation
==========================================

* Sous Github

  * Créer un repository sous Github
  * relever :abbr:`l'URL de celui-ci (par exemple : https://github.com/open-net-sarl/readthedocs.git)`.

* Sous Read the Docs

  * Cliquer **Import a Project** et sélectionner un Repository
  * Cliquer **Admin > Settings**. Vérifier l'URL du champ "Repository URL".
  * Adapter les autres champs en fonction du besoin, notamment l'édition au format PDF ou ePub, en plus de HTML
  * Cliquer **Admin > Settings > Advanced Settings**. Vérifier le niveau de confidentialité sous "Privacy Level".

  .. note::
     Cette installation minimale permet déjà de créer une documentation en ligne en éditant des fichier :abbr:`.rst (restructuredText)` directement sous Github.
     
     Ceci constitue toutefois une solution peu élégante. D'autre part, le résultat de la conversion des fichiers .rst vers html par ReadtheDocs est assez lente.

     Afin de travailler dans de meilleures conditions, nous allons procéder en complément à l'installation d'un éditeur de code connecté à Github, ainsi qu'à l'installation du moteur de génération de documentation identique à celui de ReadtheDocs `Sphinx <http://www.sphinx-doc.org/en/master/>`_.   

=============================================
Installation du système pour l'édition locale
=============================================

* Installation du moteur `Sphinx <http://www.sphinx-doc.org/en/master/>`_

  .. note::
     Sphinx a besoin de Python pour fonctionner. Sous Windows, l'installation de Anaconda constitue probablement l'option la plus simple.

  * Télécharger et installer `Anaconda <https://repo.anaconda.com/archive/Anaconda2-5.2.0-Windows-x86_64.exe>`_
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
        # initialiser la régénération automatique
        sphinx-autobuild . _build/html
        # Dès maintenant, il suffit de raffraîchir la page du navigateur (CTRL+F5) pour oubtenir la nouvelle version après quelques secondes.
        # interrompre cet automatisme avec CTRL+C


* Sous VSCode

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
    Ne pas oublier de pousser les modifications régulièrement vers Github, sans quoi le site online ne sera pas mis à jour.

================================================================
Diverses sources d'information
================================================================ 

* Sphinx - `Documentation officielle <http://www.sphinx-doc.org/en/stable/contents.html>`_
* Read the Docs - `Documentation officielle <http://docs.readthedocs.io/en/latest/getting_started.html>`_

* restructuredText

  * `Documentation edX très complète <http://draft-edx-style-guide.readthedocs.io/en/latest/ExampleRSTFile.html>`_
  * `Documentation succinte <http://udig.refractions.net/files/docs/latest/user/docguide/sphinxSyntax.html>`_
