# Caractéristiques :

.fx: bigbullet

* Dynamique
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

Peu de **cast** automatique :

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

# limite l&#39;inter-dépendance

---

# - de lignes = - de bugs

---

# - de lignes = + facile à comprendre

---

# Pas de compilation longue

---

# Evaluateur en ligne

---

# Introspection

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

