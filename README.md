[![Build Status](https://travis-ci.org/ENikS/LINQ.svg?branch=master)](https://travis-ci.org/ENikS/LINQ) 
[![Coverage Status](https://coveralls.io/repos/github/ENikS/LINQ/badge.svg?branch=master)](https://coveralls.io/github/ENikS/LINQ?branch=master)
[![npm version](https://badge.fury.io/js/linq-es5.svg)](https://badge.fury.io/js/linq-es5)
[![Downloads](https://img.shields.io/npm/dm/linq-es5.svg)](https://www.npmjs.com/package/linq-es5)
## Language-Integrated Query (LINQ) 

LINQ is a set of features that extends powerful query capabilities to any JavaScript based language. This library is a complete implementation of LINQ Enumerable class. 

The methods in this class provide an implementation of the standard query operators for querying data sources that implement Iterable<T>. The standard query operators are general purpose methods that follow the LINQ pattern and enable you to express traversal, filter, and projection operations over data in JavaScript or any related programming languages (TypeScript, CoffeeScript, etc).
Methods that are used in a query that returns a sequence of values do not consume the target data until the query object is enumerated. This is known as deferred execution. Methods that are used in a query that returns a singleton value execute and consume the target data immediately.

### Installation
```
npm install linq-es5
```

### Using
```javascript
import {asEnumerable, Range} from "linq-es5";


var count =  asEnumerable( [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] ).Where(a => a % 2 == 1).Count()

var iterable = asEnumerable(people)
               .GroupJoin(pets,
                          person => person, 
                          pet => pet.Owner,
                          (person, petCollection) => {
                              return {
                                  Owner: person.Name,
                                  Pets: asEnumerable(petCollection)
                                       .Select(pet=> pet.Name)
                                       .ToArray()
                              };
                          });

```
For more information about original implementation please visit MSDN: https://msdn.microsoft.com/en-us/library/system.linq.enumerable.aspx 

### Implementation details
This library uses Iterable iterface T[System.iterator] natively implemented by most Javascript engines for collection types (Array, Map, Set, String). As result iterations are done much faster compared to IEnumerable implementation. The code is also backwards compatible with IEnumerable implementation. 

All relevant methods are implemented with deferred  execution so no unnecessary iterations are performed. 

### Noming Convention
Method names are following original C# convention (Name starts with capital letter) for compatibility reasons. It is done so the code could be cut/pasted from C# to JavaScritp with minor reformatting.
