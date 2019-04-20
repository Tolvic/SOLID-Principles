# SOLID Principles
The Solid Principles are a set of 5 design principles in object orientated programming intended to make software design more understandable. flexible and maintainable.

## Single Responsibility Principle
A class of a method should have a single responsibilty; it should do one thing only. 

If a class or method has multiple responsibilities it becomes difficult to navigate and understand. The wider the scope of responsibilities a class or method attempts to cover, the more complex, coupled and difficult to maintain and test it will become.

Breaking different logical areas of responsibility out into separate classes/methods improves:
* readability
* maintainability
* simplicity
* testability


## Open Closed Principle 
Entities (classes or methods) should be Open for extension, but Closed for modification.

Once complete, classes should only be modified to correct bugs. New features should be added by creating new classes or methods, and inheritance or composition can be used to re-use the existing features.

This helps to prevent "breaking changes" and reduces the need to regression test; changes should not impact existing uses of the code.

### Example
The below example is sudo code. In this example we have a method within an Alarm class that sounds an alarm at a set time every day.

```csharp
setAlarm(alarmTime){
  if(time.now == alarmTime){
    playSound();
  }
}
```

If our requirements changeand we only want to play the alarm if it's a week day, rather than modifying the method defined above, we could instead write a new method to call the `setAlarm` if it is a weekday.

```csharp
weekdayAlarm(alarmTime){
  if(isWeekday(day.now)){
    setAlarm(alarmTime);
  }
}
```

Extending the functionality of this alarm class rather than modifying the `setAlarm` method means that there is no risk that we make breaking changes to other parts of the code base. 

## Liskov Substitution Principle 
Classes should be replaceable with instances of their subtypes without altering the behaviour of the application.

If `RedCar` inherits from `Car`, they should both Accelerate the same way. This will allow intances of `Car` to be replaced with `redCar`

If a class is extended/inherited, base methods should still do what they used to do. If you override the way a method functions you introduce unpredictability into the system.

Code that adheres to LSP is loosely dependent to each other and encourages code reusability. 

Code that does not adhere to the LSP is tightly coupled, creates unnecessary entanglements and can lead to unanticipated behaviours. 

When a subclass can not substitue its parent class there would have to be multiple conditional statements to determine the class or type to handle certain cases differently. If there are changes that is required then these changes would have to be applied in multiple places. Furthermore, the entanglement that is created can lead to unanticipated behaviors.

## Interface Segregation Principle
Many client-specific interfaces are better than one general-purpose interface.

the Interface Segregation Principles splits interfaces that are very large into smaller and more specific ones so that clients will only have to know about the methods that are of interest to them.

Interfaces should be tailored to a specific purpose and be as small and simple as possible. It is possible for a class to implement multiple interfaces, so there is no need to create large, complex multi-purpose interfaces - all this does is hamper reuse and increase the likelihood that a change will have a "ripple effect".

"Favour composition over inheritance" - if some part of the interface might be used in isolation from the rest, it should be a separate interface to allow this.

This principle keeps a system decoupled and thus easier to refactor, change, and redeploy

A basic example would be where you have an `Athlete` interface with methods for `swim`, `highjump` `sprint`, etc.

By implementing the `Athlete` interface for a `Swimmer`, they would have to implement methods for all of the above even though they are not campable of performing them.

Instead, there should be interfaces such as:
* `Swimmer`
* `Sprinter`
* `HighJumper`
* etc.

## Dependency Inversion

## Appendix
The below are definitions for terms that came up during my research and study of the SOLID Principles

### Interfaces
In Object Oriented Programming, an Interface is a description of all functions that an object must have. For example, anything that behaves like a light, should have a `turn_on()` method and a `turn_off()` method.

In C#, an interface contains only the signatures of methods, properties, events or indexers. A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition. 

In the following example, the class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns void.

```csharp
interface ISampleInterface
  {
      void SampleMethod();
  }
  
  
class ImplementationClass : ISampleInterface
  {
      // Explicit interface member implementation;
      void ISampleInterface.SampleMethod()
      {
          // Method Implementation
      }
      
      static Void Main()
      {
          // Declare an interface instance.
          ISampleInterface obj = new ImplementationClass();
          
          // Call the member.
          obj.SampleMethod();
       }
  }
```

An interface can inherit from one or more base interfaces. By using interfaces, you can, for example, include behaviour from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes. 

In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.

Benefits of using Interfaces:
* **Code readability**: An interface constitutes a declaration about intentions. It defines a capability of your class, what your class is capable of doing. If you implement ISortable you're clearly stating that your class can be sorted, same for IRenderable or IConvertible.
* **Code maintainability**: Interfaces helps to reduce coupling and therefore allow you to easily interchange implementations for the same concept without the underlying code being affected. You can change the implementation of a IMessage easily by defining a new class that implements the interface. Compare that to systematically replacing all references fromMessage to CMyNewMessageClass.


### Abstration

### Entities

### Concretion
