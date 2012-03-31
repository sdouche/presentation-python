# Outils

Il existe des `shells` plus évolués que *IDLE* :

* bpython
* ipython

Outils de vérification de code statique :

* pylint
* pychecker
* pep8

---

# IDE

Une liste complète : http://wiki.python.org/moin/PythonEditors

* Vim
* Emacs
* WingIDE
* PyCharm
* Komodo
* PyDev
* Netbeans
* TextMate
* Sublime Text

# Installer des librairies

# Plusieurs couches à comprendre :
* distutils
* setuptools (fork : distribute)
* easy_install (fork : pip)

# Outils :
* virtualenv
* buildout

---



# pip

L&#39;utilitaire pip permet de manipuler les packages :

    $ pip freeze
    distribute==0.6.16
    mercurial==1.8.3
    virtualenv==1.6.1
    wsgiref==0.1.2

    $ pip search pyramid
    pyramid_simpleform        - pyramid_simpleform
    pyramid                   - The Pyramid web application framework, a Pylons project
    pyramid_mailer            - Sendmail package for Pyramid
    pyramid_pyctpp2           - pyctpp2 template bindings for the Pyramid web framework
    pyramid_jinja2            - Jinja2 template bindings for the Pyramid web framework
    pyramid_socketio          - Gevent-based Socket.IO pyramid integration and helpers
    pyramid_beaker            - Beaker session factory backend for Pyramid
    pyramid_viewgroup         - An anlologue of Zope 3 "content providers" for Pyramid
    ...

    $ pip install pyramid

---

# virtualenv

L&#39;utilitaire `virtualenv` de créer un environnement virtual :

    $ virtualenv --no-site-packages newenv
    New python executable in newenv/bin/python
    Installing setuptools............done.
    Installing pip...............done.

    $ ls newenv/
    bin  include  lib

    $ ls newenv/bin/
    activate      activate.fish     easy_install      pip      python
    activate.csh  activate_this.py  easy_install-2.7  pip-2.7


---

# buildout

Outil de génération d&#39;environnement répétable

# Extensible avec des `recipes`. Il en existe pour :

* installer des applications (Apache, Nginx...)
* configurer 
* générer des scripts
* ...

# Exemple avec 2 recipes de ma société :

* sact.recipe.junkie
* sact.recipe.postgresql

--- 

# buildout - configuration basique

    !bash
    [buildout]
    develop = .

    parts = myapp

    [myapp]
    recipe = zc.recipe.egg
    eggs = myeggs

---

# pythonbrew

L&#39;utilitaire `pythonbrew` permet d&#39;installer l''interpréteur CPython dans son `$HOME` :

    $ pybrew list -k
    # available install pythons
    Python-1.5.2
    ...
    Python-2.5.5
    Python-2.6.6
    Python-2.7.1
    Python-3.0.1
    Python-3.1.3
    Python-3.2
    
    $ pybrew install 2.7.1
