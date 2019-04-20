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

## Interface Sgregation Principle 

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
