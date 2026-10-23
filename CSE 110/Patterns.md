There are patterns, they are useful?


## Factory Methods
A method for object creation in a base class that subclasses override, so code that uses the objects does not depend on their classes

## Singleton
Sometimes when there should only be ONE of something, so it's a class with a single instance with global access, sounds like global variables

## Observer
Objects subscribe to another object and are notified when it changes, abstraction, the object doesn't have to worry about updates, and leaves it to the observer.

## Adapter
Wraps a class so its interface matches what a client expects. If we have two classes that we want to fit together, we can make an adaptor class that takes in one and gives to the other, like irl adapter


### Interactive System
Instead of batch systems, which runs then terminates, interactive systems only stop when user inputs so, otherwise, it keeps running. Diagrams show states and transitions, and input is the transition between states.

Also when you make diagrams, make sure to include a key.

### Events
A detectable change or occurrence in state that the system is designed to monitor, such user input, hardware interrupt, basically, something happened.
Usually, there is an event loop where all interactions are captured and handled, although that only allows one event at a time

