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
# Access Modifiers

C# allows for control over **where** your class members can be accessed, achieved by using a set of keywords - each with a specific rule regarding that member's **accessibility**  **level****.** They are:

 - Public: No access restrictions 
 - private: Access restricted to own class (default for class members)
 - protected: Access restricted to own class, and any child class
 - internal: Access restricted to Assembly (essentially, your project's compiled .dll)

To see these in action, let's examine a simple demonstration - that is a common roadblock for new C# developers. 

![](https://s3.amazonaws.com/General_V88/boomyeah2015/codingdojo/curriculum/content/chapter/private-access.png)

Here, I am attempting to  **access**  the Color field from a  **Vehicle**  in my  **Program**  class. And HEY! the compiler is telling me that it is inaccessible. This is because even though I haven't yet listed one, there is a default member accessibility level:  **private**, which means that you may only refer to that member  _from the class from which it was defined_ - in this example, that would mean only from within the body of the Vehicle class. If I wish to access Color and MaxNumPassengers from my Program class, I would have to add a keyword to the member definition:  **public**, which has  _no access restrictions_**.  
**

Our Vehicle class now looks like so:

```javascript 
class Vehicle
{
    public int MaxNumPassengers;
    public string Color;
    public Vehicle(int maxPass, string color)
    {
        MaxNumPassengers = maxPass;
        Color = color;
    }
}
```
Now I am able to access these fields, and print their values to the Console.

![](https://s3.amazonaws.com/General_V88/boomyeah2015/codingdojo/curriculum/content/chapter/public-access.png)

## Encapsulation

Of course, you will not want every class member to be public - in fact, you will want to keep all members as restricted as you are able. The idea is to follow a common OOP principle of  **encapsulation**: to hide internal implementation from outside code - as much as possible - and to only publicly provide what is essential. By making Color and MaxNumPassengers  **public**, we are allowing read and write access to these fields from anywhere. Generally, this is not desirable. A common way to deal with this problem, is to use  **properties**  to be a public "wrapper" for our private fields. By using only a  **getter**, we can provide public read-only access to our private fields.

Let's see how we may modify the Vehicle class to achieve this:
```javascript
class Vehicle
{
    private int maxNumPassengers;
    private string color;
    public int MaxNumPassengers
    {
        get { return maxNumPassengers; }
    }
    public string Color
    {
        get { return color; }
    }
    public Vehicle(int maxPass, string col)
    {
        maxNumPassengers = maxPass;
        color = col;
    }
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4OTkxMjYxNCwtMTMzNzY0NjgxLC0xNj
gyOTI3Njg5XX0=
-->