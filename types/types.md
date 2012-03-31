# Types de base

# Simples et puissants :

* bool
* int, float, complex
* str, unicode
* tuple
* set
* dictionary
* xrange
* file
* exception, module, class, function

---

# Exemples

    !python
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

# Méthodes «magiques»

* object.\_\_new__(self, other)
* object.\_\_del__(self, other)
* object.\_\_init__(self, other)
* object.\_\_repr__(self, other)
* object.\_\_str__(self, other)
* object.\_\_eq__(self, other)
* object.\_\_cmp__(self, other)
* object.\_\_get__(self, other)
* object.\_\_set__(self, other)
* object.\_\_call__(self, other)
* ...

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

# Autres types disponibles

# Types dans les modules :

* heapq
* collections (namedtuple, deque, coutner, OrderedDict, defaultdict)
* bisect
* array
* sched
* queue
* ...
