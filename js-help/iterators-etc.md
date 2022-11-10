# Iterables and Iterators

- Iterable objects are objects that can be iterated over with `for(const element of iterableObj)`
- Iterables must implement the Symbol.iterator method.
- ES6 specification uses @@iterator to reference Symbol.iterator. There is no @@iterator, and wherever you see it, read it as [Symbol.iterator].

- When an iterable is iterated over with the for/of loop, the [Symbol.iterator]() method is invoked.

-the square brackets around the “Symbol.iterator” indicate that it is a computed property name, or a value that is returned when JavaScript accesses “Symbol.iterator”. So the method name is computed by JavaScript, and the returned value is the method’s name that is used, but which is not known in order to hard code it. The presence of this method is what makes a data structure iterable, and it does so because the method returns the iterator interface.

- Using an iterable in for/of loop like `for(const element of iterableObj)` invokes the [Symbol.iterator]() method which returns the `iterator` object which accesses the values of the iterable object. The “iterator” is what iterates over the data structure by invoking a next() method which returns another object containing the desired value.

- In order to be iterable, an object must implement the @@iterator method, meaning that the object (or one of the objects up its prototype chain) must have a property with a @@iterator key which is available via constant Symbol.iterator:
