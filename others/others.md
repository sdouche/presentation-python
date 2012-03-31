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
        re turn wrapper

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

    for key in {&#39;one':1, 'two':2}:
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

    S = []
    for x in range(101):
        if x**2 > 3:
            S.append(2*x)

    T = [x+y for x in 'flower' for y in 'pot']

    U = [x+y for x in 'flower' for y in 'pot' if x != 'w' and y != 'o' ]

Existe aussi pour les set (set comprehension) et dictionary (dictionary comprehension).

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
