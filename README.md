# Liskov Substitution Principle (LSP)

The **`Liskov Substitution Principle (LSP)`** is one of the SOLID principles, and it states that objects of a derived class should be able to replace objects of the base class without affecting the correctness of the program. In other words, if a class is a subclass (derived class) of another class (base class), it should be possible to use objects of the derived class wherever objects of the base class are expected.

Here's a C# example to illustrate the Liskov Substitution Principle using a geometric shape hierarchy:

```csharp
// Base class representing a geometric shape
public class Shape
{
    public virtual double CalculateArea()
    {
        return 0;
    }
}

// Derived class representing a rectangle
public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea()
    {
        return Width * Height;
    }
}

// Derived class representing a square
public class Square : Shape
{
    public double SideLength { get; set; }

    public override double CalculateArea()
    {
        return SideLength * SideLength;
    }
}
```

In this example, we have a base class **`Shape`** with a virtual method **`CalculateArea()`**, which returns 0 as a default implementation. We then have two derived classes, **`Rectangle`** and **`Square`**, each of which overrides the **`CalculateArea()`** method to calculate the area of the respective shape.

Now, let's demonstrate the Liskov Substitution Principle in action:

```csharp
static void Main(string[] args)
{
    Shape shape1 = new Rectangle { Width = 4, Height = 3 };
    Shape shape2 = new Square { SideLength = 5 };

    Console.WriteLine($"Area of the rectangle: {shape1.CalculateArea()}"); // Outputs 12
    Console.WriteLine($"Area of the square: {shape2.CalculateArea()}");    // Outputs 25
}
```

In this code, we create objects of both **`Rectangle`** and **`Square`** classes and store them in variables of type **`Shape`**, the base class. We can then call the **`CalculateArea()`** method on these objects without knowing their specific derived types. This demonstrates the Liskov Substitution Principle because objects of the derived classes can be used interchangeably with objects of the base class without affecting the correctness of the program.

This principle promotes polymorphism and helps ensure that derived classes maintain a compatible interface with the base class, making your code more flexible and maintainable.
