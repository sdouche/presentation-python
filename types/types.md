# Types disponibles

# Types de bases :

* bool
* int, float, long, complex
* str, unicode
* tuple
* set, frozenset
* dictionary
* xrange
* file
* exception, module, fonction
* memoryview
* with

---

# Types disponibles

# Types dans les modules :

* heapq
* collections (namedtuple, deque, coutner, OrderedDict, defaultdict)
* bisect
* array
* sched
* queue
* ...

---

mystruct = [1. 2, 3]
mystruct = [{1: 'a'}, {2: 'b'}]
mystruct = [{1: 'a'}, [{2: 'b'}, (1, 2)]]

new_event = {"description": "test",
             "name": "Les Concerts & ouvertures praguoises",
             "sessions": [ { "showDateTimeStart": datetime.datetime.utcnow() } ],
             "updated": datetime.datetime.utcnow(),
             "venue": { "name": "Opera",
                        "pCode": "21000",
                        "town": "Dijon",
                        "way": "11 Boulevard de Verdun" }}

---

Chaque type vient avec une API

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

Un décorateur en Python permet d&#39;injecter ou de modifier le comportement d&#39;une fonction / classe.
Ruby est suffisamment flexible pour ne pas en avoir besoin.

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

closure

coroutine


