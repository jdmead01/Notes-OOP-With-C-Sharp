# OOP With C#

Object Oriented Programming (OOP) is a key paradigm of the C# language and is extensively used in the ASP.NET Core web-framework, so it is a critical skill for us to learn. The main focal point of OOP in C# is class creation. Classes define what objects we can build, how we can interact with them, and how they themselves interact with our program. A simple way to look at classes is as a blueprint of functions and properties that we want as an instance of this class, AKA an Object, to hold. It may be easier to see as we begin working with them, so let's jump right into basic object creation.

```javascript 
//Make sure to include the Vehicle class separate from the Program class
public class Vehicle
{
    //Accessibility of class members is defaulted to private
    //so we must add the public keyword to anything we
    //want to allow outside access to.
    
    // this unassigned integer will default to 0
    public int NumPassengers;
}
```
This is all it takes to define a class. In order to create an object of a class, though, we must invoke our class as a new object reference. **Take special note where we put each piece of this code in our Program.cs file!**
```javascript
public class Program
{
    public static void Main(string[] args)
    {
        // Notice the type for the new object reference
        // is the same as the class name
        Vehicle myVehicle = new Vehicle();
        Console.WriteLine($"My vehicle is holding {myVehicle.NumPassengers} people");
    }
}
```
With this in our Main function, we have declared the variable of myVehicle to be an instance (or object) of the class Vehicle. We also added a field of NumPassengers to the class, that becomes part of the object variable when it is created. If we wanted to pass a variable to this object when creating it to set some of its data members, such as the NumPassengers field, we need to include a function inside the class called a constructor. As the name implies, constructors are functions that exist to "construct" instances of a class. A constructor is called the moment an object is created using the **new** keyword and just requires adding a function with the same name as the class.
```javascript
public class Vehicle
{
     public int NumPassengers;
     //Notice the Constructor function doesn't need
     //a return type or the static keyword
     public Vehicle(int val)
     {
          NumPassengers = val;
     }
}
```
```javascript
public class Program
{
    public static void Main(string[] args)
    {
        //Adding a value to the object; then passes it to the constructor
        Vehicle myVehicle = new Vehicle(7);
        Console.WriteLine($"My vehicle is holding {myVehicle.NumPassengers} people");
    }
}
```
If we want all instances of our class to have some initial value, we can achieve this by providing a Constructor that takes no arguments, but initializes values within the Constructor body.
```javascript
public class Vehicle
{
     public int NumPassengers;
    
     public Vehicle()
     {
          NumPassengers = 5;
     }
}
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMzc2NDY4MSwtMTY4MjkyNzY4OV19
-->