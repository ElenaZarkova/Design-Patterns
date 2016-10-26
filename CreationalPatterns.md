## Singleton
* The Singleton class is a class that is supposed to have only one (single) instance
* Intent - Ensuring a class only has one instance, and providing a global point of access to it. Encapsulated "just-in-time initialization" or "initialization on first use"
* Motivation - Application needs one, and only one, instance of an object. Additionally, lazy initialization and global access are necessary
* Applicability 
    * There must be exactly one instance of a class, and it must be accessible to clients from a well-known access point.  
    * When the sole instance should be extensible by subclassing, and clients should be able to use an extended instance without modifying their code.
* Known uses - Access window manager / file system / console, access global application logger / DC / Mapper
* Participants - Singleton defines an Instance operation that lets clients access its unique instance. 
    Instance is a class operation. It may be responsible for creating its own unique instance.  
* Consequences
    * Controlled access to sole instance.
    * Permits refinement of operations and representation.
    * More flexible than class operations.
    * Default (not thread-safe) implementation should not be used in multi-threaded environments (e.g. ASP.NET)
    * Singleton introduces tight coupling among collaborating classes
    * Singletons are difficult to test

* Structure - Makes the class of the single instance responsible for access and "initialization on first use". The single instance is a private static attribute. The accessor function is a public static method.
* Related patterns - Abstract Factory, Builder

## Simple Factory
* Simple Factory is a class that encapsulates object creation logic
* Intent - Hide complex object creation logic.
* Motivation - New obbjects have to be created and that logic needs to be encapsulated. Also, that logic should nbe extracted in a new class to follow the single responsisbility principle.
* Applicability - There is an abstract class or inserface and derived classes need to be instantiated. In different cases different class is needed but all have the same interface.
* Examples - The application works with shapes, all derived from an abstract shape class (or interface). Different type of shape is created based on user input.
* Implementation
    * The client needs a product, but instead of creating it directly using the new operator, it asks the factory object for a new product, providing the information about the type of object it needs.
    * The factory instantiates a new concrete product and then returns to the client the newly created product(casted to abstract product class).
    * The client uses the products as abstract products without being aware about their concrete implementation.
* Consequences
    * Abstarcted logic for object creation. 
    * The class that uses the factory has no information about the specific class being instatiated, it uses it through interface. We have separation of concerns and single responsibility principle.
* Related patterns - Factory Method, Abstract Factory

## Abstract Factory
* The Abstract Factory Pattern defines interface for creating sets of linked objects, without knowing their concrete classes.
* Intent - Abstraction in object creation - creation of a family of related objects
* Motivation - Used in systems that are frequently changed
* Applicability 
    * The system needs to be independent from the way the products it works with are created.
    * The system is or should be configured to work with multiple families of products.
    * A family of products is designed to work only all together.
    * The creation of a library of products is needed, for which is relevant only the interface, not the implementation.
* Consequences
    * Provides flexible mechanism for replacement of different sets
    * Isolates concrete classes.
    * Promotes consistency among products. 
* Related patterns - Simple Factory, Strategy