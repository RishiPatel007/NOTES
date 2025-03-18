# Coupling

## ***Definition***
- `Coupling` refers to the degree of interdependence between software modules. 
- `High coupling` means that modules are closely connected and changes in one module may affect other modules. 
- `Low coupling` means that modules are independent, and changes in one module have little impact on other modules.

## ***Types Of Coupling***

- ***Data Coupling:*** If the dependency between the modules is based on the fact that they communicate by passing only data, then the modules are said to be data coupled. In data coupling, the components are independent of each other and communicate through data. Module communications don’t contain tramp data. 

- ***Stamp Coupling*** In stamp coupling, the complete data structure is passed from one module to another module.

- ***Control Coupling:*** If the modules communicate by passing control information, then they are said to be control coupled. For Example : if-else or switch

- ***External Coupling:*** In external coupling, the modules depend on other modules, external to the software being developed or to a particular type of hardware.

- ***Content Coupling:*** In a content coupling, one module can modify the data of another module, or control flow is passed from one module to the other module. This is the worst form of coupling and should be avoided.

- ***Temporal Coupling:*** Temporal coupling occurs when two modules depend on the timing or order of events, such as one module needing to execute before another. This type of coupling can result in design issues and difficulties in testing and maintenance.



# Cohesion

## ***Definition*** 
- `Cohesion` refers to the degree to which elements within a module work together to fulfill a single, well-defined purpose. 
- `High cohesion` means that elements are closely related and focused on a single purpose.
- `Low cohesion` means that elements are loosely related and serve multiple purposes.

## ***Types of Cohesion***
- **Coincidental Cohesion (Lowest Level)**
    - Elements within a module are loosely connected with no meaningful relationship
    - Components perform unrelated tasks
    - Considered the worst type of cohesion
    - Example: A utility class with methods that have no logical connection
    
- **Logical Cohesion**
    - Module elements are related through a broad logical category
    - Components perform similar types of operations
    - Slightly better than coincidental cohesion
    - Example: A utility class with methods for different types of data validation

- **Temporal Cohesion**
    - Module elements are grouped because they are executed at the same time
    - Components are performed in a specific time frame or sequence
    - Example: Initialization methods that set up a system at startup

- **Procedural Cohesion**
    - Module elements follow a specific sequence of steps to accomplish a task
    - Components are organized based on a procedure or algorithm
    - Example: A method that processes a transaction with distinct steps
    
- **Communicational Cohesion**
    - Module elements operate on the same data set or input/output
    - Components share and manipulate related data
    - Example: Methods in a customer management class that work with customer information
    
- **Sequential Cohesion**
    - Module elements perform related tasks where the output of one becomes the input of another
    - Components are connected through a sequential data flow
    - Example: A method that reads data, processes it, and then writes the result
    
- **Functional Cohesion (Highest Level)**
    - Module elements work together to perform a single, well-defined function
    - Components have a clear, singular purpose
    - Considered the most desirable type of cohesion
    - Example: A method that calculates the area of a specific geometric shape


---

# Best Practice

Both coupling and cohesion are important factors in determining the maintainability, scalability, and reliability of a software system.
- `High coupling and low cohesion` can make a system difficult to change and test.
- `Low coupling and high cohesion` make a system easier to maintain and improve.

## Advantages of low coupling

- Improved maintainability: Low coupling reduces the impact of changes in one module on other modules, making it easier to modify or replace individual components without affecting the entire system.
- Enhanced modularity: Low coupling allows modules to be developed and tested in isolation, improving the modularity and reusability of code.
- Better scalability: Low coupling facilitates the addition of new modules and the removal of existing ones, making it easier to scale the system as needed.

## Advantages of high cohesion

- Improved readability and understandability: High cohesion results in clear, focused modules with a single, well-defined purpose, making it easier for developers to understand the code and make changes.
- Better error isolation: High cohesion reduces the likelihood that a change in one part of a module will affect other parts, making it easier to
- Improved reliability: High cohesion leads to modules that are less prone to errors and that function more consistently, 
- leading to an overall improvement in the reliability of the system.