More readable code is better, but how?

SOLID

### SRP - Single Responsibility Principle
A class should only be responsible for one thing, it should do its own calculations, and not do calculations of another, or have others to work for it that it isn't meant to do. To check, write The (class) (method)s itself, and if it sounds wrong, then add a doer to do it for them.

### Open-closed Principle
Classes should be open for extension but closed for modification, which means you should be extending the class with interfaces, which extends functionality with additional implementations

### Liskov Substitution Principle
Properties of a class should hold on subclasses, as in the property should be in all the subclasses. Example electric car no have engine, so start engine shouldn't be in base class car

### Interface Segregation Principle
Clients shouldn't have to implement interfaces they don't use, or to depend on methods they don't use. Example, shape includes area(), and 3d shapes have volume(), but don't put volume in shape, make 3dShape and put it there

### Dependency Inversion Principle
High level shouldn't import anything from low level, they should both import from interface
Abstraction shouldn't depend on details, details should depend on abstractions. Can be overdone.