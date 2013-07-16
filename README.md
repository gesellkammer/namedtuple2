namedtuple2
===========

A drop-in replacement for Python's collections.namedtuple with support for default values

    >>> Point = namedtuple('Point', 'x y')
    >>> Point.__doc__                   # docstring for the new class
    'Point(x, y)'
    >>> p = Point(11, y=22)             # instantiate with positional args or keywords
    >>> p[0] + p[1]                     # indexable like a plain tuple
    33
    >>> x, y = p                        # unpack like a regular tuple
    >>> x, y
    (11, 22)
    >>> p.x + p.y                       # fields also accessable by name
    33
    >>> d = p._asdict()                 # convert to a dictionary
    >>> d['x']
    11
    >>> Point(**d)                      # convert from a dictionary
    Point(x=11, y=22)
    >>> p._replace(x=100)               # _replace() is like str.replace() but targets named fields
    Point(x=100, y=22)

    >>> Point = namedtuple('Point', 'x y=10')
    >>> p = Point(20)
    Point(x=20, y=10)

When using strings, use " for the string, ' for the fields, as in the below example

    >>> Person = namedtuple('Person', 'surname name="UNKNOWN"')
    >>> p = Person("Cage", "John")
    Person(surname='Cage', name='John')
    >>> p = Person("Cage")
    Person(surname='Cage', name='UNKNOWN')
