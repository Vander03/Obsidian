https://brook-jeynes.gitbook.io/study-guides/v/cab/cab302-or-2022-s1#week1

## Classes

Classes can be concrete or abstract and are used to create objects. **Objects** are instances of classes

```java
public class Cylinder implements Shape { // visible class implementing Shape interface

    private double radius; // local variables used for calculations
    private double height;

    public Cylinder(double radius, double height) { // constructor applying values of new object to its fields
        this.radius = radius;
        this.height = height;
    }

    @Override
    public double volume() {
        return Math.PI * radius * radius * height; // clled with Cylinder.volume
    }

    @Override
    public double surfaceArea() {
        return 2 * Math.PI * radius * (radius + height);
    }
}
```

## Interface

```java
package shapes;

/* Interface laying out structure for similar classes to implement differing methods of*/
public interface Shape {
    double volume();

    double surfaceArea();
}
```


