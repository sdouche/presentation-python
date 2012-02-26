# Mon parcours

Jeune (1985 - 1995) :

* BASIC
* C
* Turbo Pascal
* Assembleur x86

Moins jeune (1996 - 2002) :

* Python / Ruby / Perl / PHP
* REBOL
* ADA / Eiffel
* Erlang / Lisp / forth / Pike
* Tcl/Tk / Unix Shell
* Smalltalk / Java / Objective C

Vieux (2011) :

* Scala
* OCaml
* Haskell
* Coffeescript
* Guile
* Go
* Lua

---

# Dans mon entreprise

Nous fournissons des **appliances**.

Le code actuel :

* Python - **70k** SLOC
* C - **25k** SLOC
* Guile (Scheme) - **2.5k** SLOC

Il y&#39;a 1 an : **120k** SLOC

# SLOC total (3,5 ans)

Entre **300k** et **400k** SLOC

# Moyenne de développeurs

Entre 4 et 5

---

# Un langage est un univers

.fx: image

![](universe.jpg)

---

# Comprendre un univers

# Chaque langage est une *vision* du développement

.fx: bigbullet

* une syntaxe
* une sémantique
* choix technique
* une philosophie

--- 

# Tout est question d&#39;équilibre

.fx: title

---

# import antigravity - xkcd.com/353/

.fx: image

![](xkcd.png)

--- 

# Citations

> “Controlling complexity is the essence of computer programming.”
(Brian Kernigan) 
 
> “Complexity kills.  It sucks the life out of developers, it makes products difficult to plan, build and test, it introduces security challenges, and it causes end-user and administrator frustration.”
(Ray Ozzie) 
 
> “Everything should be made as simple as possible, but not simpler.”
(Albert Einstein)

---

# philosophie

# lisibilité

# Homogénéité

# Explicite

# Concision

# simplicité

# extensible

# battery included

---

# Ma citation préférée

> Ce qui est simple doit rester simple, ce qui est compliqué doit est possible

--- 

# Résultat

# Un langage :

* expressif (pseudo code)
* consistent
* orthogonal (manuel de référence : ~100 pages)

--- 

# 31 mots clés

.fx: image

![](python-keyword.png)

---

# Builtins

.fx: image

![](python-builtins.png)

---

# PEP : Python Enhancement Proposal

.fx: image

![](python-pep.png)

---

# Grammaire du C

.fx: image

![](c-grammar.jpg)

---

# Grammaire du Javascript

.fx: image

![](javascript-grammar.jpg)

---

# Grammaire de Ruby 1.8.4

.fx: image

![](ruby-grammar.jpg)

---

# Grammaire de Java 1.5

.fx: image

![](java-grammar.jpg)

---

# Grammaire de Python 2.3.3

.fx: image

![](python-grammar.jpg)

---

# Sémantique (paradigme)

.fx: bigbullet

* structuré
* objet
* fonctionnel

---

# Structuré simple

Format script (fichier sample.py) :

    !python
    print "hello world!"

Exécution :

    $ python sample.py
    hello world!

---

# Structuré avec méthode

Transformation en code structuré avec des méthodes : 

    !python
    def hello_world():
        print "hello world!"

    if __name__ == '__main__':
        hello_world()

Je peux utiliser la méthode en important mon fichier :

    !python
    from sample import hello_world
    hello_world()

---

# objet

Transformation en code objet :

    !python
    class MyClass(object):
       def hello_world(self):
           print "hello world!"
 
    if __name__ == '__main__':
        test = MyClass() 
        test.hello_world()

---

# Fonctionnel

Python implèmente `lambda`, `map`, `filter`, `reduce` :

    !python
    total = reduce(lambda a, b: (0, a[1] + b[1]), items)[1]

Les itérateurs :

    !python
    L = [1,2,3]
    it = iter(L)
    it.next()

Un code plus `pythonic` :

    !python
    L = [1,2, 3]
    for i in L:
    ...

Générateur d&#39;expression (retourne un itérateur) :

    !python
    stripped_iter = (line.strip() for line in line_list)

List comprehension (retourne un objet liste) :

    !python
    stripped_list = [line.strip() for line in line_list]

Module `functools`, `itertools`, `operator`.

---

# pythonic / unpythonic

---

# Exemple

unpythonic :

    !python
    i = 0
    while i < mylist_length:
        do_something(mylist[i])
        i += 1

pythonic :

    !python
    for element in mylist:
        do_something(element)

pythonic avec gestion de l&#39;indice :

    !python
    for indice, element in enumerate(mylist):
        do_something(element)
        print indice

---

# Caractéristiques :

.fx: bigbullet

* Dynamique
* Fortement typé
* Duck typing

---

# Dynamique

# variable -> objet -> type

Inutile de typer la variable, mais seulement l&#39;objet :

    !python
    a = 1            # objet int
    a = "My string"  # objet string

Le type est vérifié à l&#39;éxécution.

---

# Faiblement typé mais...

Pas de **cast** automatique :

    !python
    >>> a = 1
    >>> b = "my string"
    >>> a + b
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: unsupported operand type(s) for +: 'int' and 'str'

.notes: le typage est une échelle, plus ou moins typé

---

# Duck typing

# Vérifie uniquement que la méthode appelée existe et non le type.

.fx: centerquote

> When I see a bird that walks like a duck and swims like a duck
> and quacks like a duck, I call that bird a duck


---

# Rappel sur le type statique

# Avantages :

* Clarification
* Détection d&#39;erreur à la compilation
* Performance
* Refactoring automatique

# Défauts :

* Création d&#39;interfaces incompatibles
* Ne pousse pas la factorisation
* Boilerplate
* Refactoring plus dangereux

---

# Un exemple simple

    !python
    class Duck:
        def quack(self):
            print("Quaaaaaack!")
        def feathers(self):
            print("The duck has white and gray feathers.")
 
    class Person:
        def quack(self):
            print("The person imitates a duck.")
        def feathers(self):
            print("The person takes a feather from the ground and shows it.")
        def name(self):
            print("John Smith")
 
    def in_the_forest(duck):
        duck.quack()
        duck.feathers()
 
    def game():
        donald = Duck()
        john = Person()
        in_the_forest(donald)
        in_the_forest(john)
 
    game()

---

# Polymorphisme

# Le Duck Typing permet le polymorphisme.

Comparable au :

* structural type
* interface
* template

---

# **Défauts**

---

# Nécessite de mieux connaitre le fonctionnel

---

# Collage de code non vérifié

---

# Facilite le code spaghetti

---

# Plus facile de pousser un bug en production

---

# Pas de refactoring automatique

---

# Performance

---

# Aucun avertissement du compilateur

---

# **Avantages**

---

# Simple

---

# Pousse à la simplicité

---

# Souple

---

# Généricité

---

# API simplifiée

---

# Collage de code simplifié

---

# Simplifie le refactoring

---

# limite l&#39;inter-dépendance

---

# - de lignes = - de bugs

---

# - de lignes = + facile à comprendre

---

# Pas de phase de compilation

---

# Introspection

---

# Evaluateur en ligne

---

# Compenser les lacunes

Avec :

* Documentation (entrée, sortie, exception)
* Doctest
* Refactorer souvent
* Strong typing vs Strong testing

---

# First class function / First class object

Entité qui peut :

* Passée en paramêtre
* Passée en argument
* Retournée comme valeur de retour
* Incorporée dans une structure de donnée

En python, tous les objects sont *first class*.

---

# Exemple 1

On peut écrire :

    !python
    def sumOfSquares(a, b):
        return a**2 + b**2

    def sumOfCubes(a, b):
        return a**3 + b**3

    def sumOfNegatives(a, b):
        return (-a) + (-b)

---

# Exemple 1

Un code *pythonic* :

    !python
    def square(a):
        return a**2

    def cube(a):
        return a**3

    def negative(a):
        return -a

    def sum (a, b, function):
        return function(a) + function(b)

Un code *pythonic* avec le style fonctionnel :

    !python
    sumOfSquares = lambda a, b: sum(a, b, square)
    sumOfCubes = lambda a, b: sum(a, b, cube)

---

# Exemple 2

Je souhaite afficher du texte en spécifiant la couleur :

    !python
    from fabric.colors import *

    def display(msg, color=green):
        print(color(msg))

---

# Exemple 3

Un dispatcher :

    !python
    def handle_one():
        return 'one'

    def handle_two():
        return 'two'

    def handle_default():
        return 'unknown'

    cases = {
        'one': handle_one,
        'two': handle_two,
        'three': lambda: 'three',
    }

    for i in ('one', 'two', 'three', 'four', ):
        handler = cases.get(i, handle_default)
        print handler()

---

# EAFP vs LBYL

Python pousse à la programmation :

*EAFP* (Easier to Ask for Forgiveness than Permission)

et non : 

*LBYL* (Look before you Leap)

    !python
    import sys
    
    try:
        f = open('myfile.txt')
        s = f.readline()
        i = int(s.strip())
    except IOError as (errno, strerror):
        print "I/O error({0}): {1}".format(errno, strerror)
    except ValueError:
        print "Could not convert data to an integer."
    except:
        print "Unexpected error:", sys.exc_info()[0]
        raise

---

# Types de base

# Simples et puissants :

* bool
* int, float, complex
* str, unicode
* tuple
* set, frozenset
* dictionary
* xrange
* file
* exception, module, fonction

---

# Méthodes spéciales

# Basique

* object.\_\_new__(self, other)
* object.\_\_del__(self, other)
* object.\_\_init__(self, other)
* object.\_\_repr__(self, other)
* object.\_\_str__(self, other)
* object.\_\_eq__(self, other)
* object.\_\_cmp__(self, other)
* object.\_\_get__(self, other)
* object.\_\_set__(self, other)
* ...

---

# Méthodes spéciales

# Appelable

* object.\_\_call__(self, other)

# Conteneur

* object.\_\_len__(self)
* object.\_\_getitem__(self)
* object.\_\_setitem__(self)
* object.\_\_delitem__(self)
* object.\_\_iter__(self)

# Context manager

* object.\_\_enter__(self)
* object.\_\_exit__(self)

---

# Exemples

    !python
    def __repr__(self):
        return repr(self.data) 

    def __cmp__(self, dict):                      
        if isinstance(dict, UserDict):            
            return cmp(self.data, dict.data)      
        else:                                     
            return cmp(self.data, dict)           
    
    def __len__(self):
        return len(self.data)

    def __delitem__(self, key):
        del self.data[key]

---

# Decorateur

Un décorateur permet d&#39;injecter ou de modifier le comportement d&#39;une fonction / classe.

Un décorateur simple :

    !python
    def decorator(func):
        func.is_decorate = True
        return func

    @decorator
    def decorate():
        pass

    decorate.is_decorate

Un décorateur avec un argument :

    !python
    def decorator(attempt):
        def wrapper(func):
            func.attempt = attempt
            return func
        return wrapper

---

# Quelques cas d&#39;utilisation :

* Memoize
* Cache
* Ajout facile de méthodes à une classe
* Compteur
* Deprecation Warnings
* Pre / post condition
* Profiling / debug
* Synchronisation
* Vérification de type
* ACL
* Gestion d&#39;évenement
* Singleton
* ...

---

# Itérateur

# Beaucoup de types de base sont itérables.

On retrouve la philosophie *Faire les choses d&#39;une seule manière* :

    !python
    for element in [1, 2, 3]:
        print element

    for element in (1, 2, 3):
        print element

    for key in {'one':1, 'two':2}:
        print key

    for char in "123":
        print char

    for line in open("myfile.txt"):
        print line

--- 

# Itérateur

Créer un type itérable :

    !python
    class fibnum:
        def __init__(self):
            self.fn2 = 1
            self.fn1 = 1

        def next(self):
            (self.fn1,self.fn2,oldfn2) = (self.fn1+self.fn2,self.fn1,self.fn2)
            return oldfn2

        def __iter__(self):
            return self

    f = fibnum()
    for i in f:
        print i
        if i > 20:
            break

---

# Générateur

Utilisation du mot clé `yield` :

    !python
    def fonction(x):
        while 1:
            yield x
            x = x + 1

     >>> gen = fonction(2)
     >>> gen.next()

---

# List comprehension

Une *list comprenhension* renvoie une liste.

    !python
    S = [2*x for x in range(101) if x**2 > 3]

    T = [x+y for x in 'flower' for y in 'pot']

    U = [x+y for x in 'flower' for y in 'pot' if x != 'w' and y != 'o' ]

Existe aussi pour les set (set comprehension) et dictionary (dictionary comprehension).

---

# Droit

# Pas de notion privé / public.

La convention est de mettre un **_** pour indiquer une méthode privée.

---

# Context manager

Sucre syntaxique qui simplifie le code :

    !python
    with open('foo.txt', 'w') as f:
        f.write('hello!')

Au lieu de :

    !python
    f = open('foo.txt', 'w')
    f.write('hello!')

---

# Lien avec le C

Module ctypes pour utiliser facilement le C :

    !python
    from ctypes import *
    cdll.LoadLibrary("libc.so.6")
    libc = CDLL("libc.so.6")

Projets cython / SWIG.

---

# zope.interface

Création d&#39;une interface :

    !python
    import zope.interface
    class IFoo(zope.interface.Interface):
        """Foo blah blah"""
        
        x = zope.interface.Attribute("""X blah blah""")

        def bar(q, r=None):
           """bar blah blah"""

Utilisation : 

    !python
    class Foo:
        zope.interface.implements(IFoo)

        def __init__(self, x=None):
            self.x = x

        def bar(self, q, r=None):
            return q, r, self.x

        def __repr__(self):
            return "Foo(%s)" % self.x

---

# **Conclusion**

---

# Plaisir de coder

---

# Efficacité

---

# Permet de coder des scripts de 5 SLOC aux projets de 150k SLOC

---

# Merci :)
