# 04: Einführung in Objekte

## Kurze Begriffserklärung

Quelle: [stackhowto.com](https://stackhowto.com/difference-between-instantiating-declaring-and-initializing/)

### Declaration
> Declaring a variable means the first “mention” of the variable, which tells the compiler “Hello, I am here and can be used”. 
> In a statically typed language like Java, this also means that the declared type of the variable is determined. 
> The value itself is not determined during the declaration.
```java
String name;
int nbr;
```

### Initialization
> The term initialization usually means the first assignment of a value to a variable.
```java
String name = "Thomas";
int nbr = 5;
```

### Instantiation
> The term instantiation actually has nothing to do with assigning a value to a variable, even if a new object is sometimes instantiated when a variable is initialized.
> The term simply means the creation of a new object, i.e. an instance, from a class.
```java
String name = new String("Thomas");
```

## Modifier

Quelle: [w3schools.com](https://www.w3schools.com/java/java_modifiers.asp)

### Access-Modifier

| Modifier  | Beschreibung                                                                                     |
|-----------|--------------------------------------------------------------------------------------------------|
| public    | The code is accessible for all classes                                                           |
| private   | The code is only accessible within the declared class                                            |
| protected | The code is accessible in the same package and subclasses.                                       |
| default   | The code is only accessible in the same package. This is used when you don't specify a modifier. |

### Non-Access-Modifier

| Modifier | Beschreibung                                                                                                      |
|----------|-------------------------------------------------------------------------------------------------------------------|
| final    | The class cannot be inherited by other classes                                                                    |
| abstract | The class cannot be used to create objects (To access an abstract class, it must be inherited from another class. |


## #1 Einfache Objekte und Veerbung
**Lernziele:**
* eine Klasse erzeugen 
* eine Klasse aufrufen
* einfache Veerbung
* Polymorphie (Überschreiben von Methoden)
* die Verwendung von `this`
* die Verwendung von `super`

```java
// main.java
public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal();
        myAnimal.makeSound();

        Dog myDog = new Dog();
        myDog.makeSound();

        Cat myCat = new Cat();
        myCat.makeSound();

        myCat.compareToAnimal();
    }
}
```

```java
// Animal.java
public class Animal {
    public boolean isPet;

    public Animal() {
        System.out.println("## in constructor of Animal");
        this.isPet = false; // it doesn't exist for our cats or dogs
    }

    public void makeSound() {
        System.out.println("Yes, animal usually make sounds");
    }

}
```

```java
// Cat.java
public class Cat extends Animal {

    public Cat() {
        System.out.println("## in constructor of Cat");
        this.isPet = true;
    }

    @Override
    public void makeSound() {
        System.out.println("meow meow");
    }

    public void compareToAnimal() {
        System.out.println("--- Animal ---");
        super.makeSound();
        System.out.println("is alive: " + super.isPet);

        System.out.println("--- Cat ---");
        this.makeSound();
        System.out.println("is alive: " + this.isPet);
    }
}
```
```java
// Dog.java
public class Dog extends Animal {

    public Dog() {
        System.out.println("## in constructor of Dog");
        this.isPet = true;
    }
    
    @Override
    public void makeSound() {
        System.out.println("woof woof");
        this.isPet = true;
    }

    public void compareToAnimal() {
        System.out.println("--- Animal ---");
        super.makeSound();
        System.out.println("is alive: " + super.isPet);

        System.out.println("--- Cat ---");
        this.makeSound();
        System.out.println("is alive: " + this.isPet);
    }

}
```

## #2 komplexere Vererbung von Klassen

**Lernziele:**
* Erweiterte Veerbung
* Modifikatoren für Attribute
* Getter und Setter
* Konstruktorverkettung

```java
// main.java
public class Main {
    public static void main(String[] args) {
        Vehicle myVehicle = new Vehicle();
        System.out.println("-- myVehicle:");
        System.out.println("number of wheels: " + myVehicle.getNumberOfWheels());
        System.out.println("max Speed: " + myVehicle.getMaxSpeed());
        myVehicle.setMaxSpeed(150);
        System.out.println("max Speed: " + myVehicle.getMaxSpeed());

        Car myCar = new Car("blue");
        System.out.println("-- myCar:");
        System.out.println("number of wheels: " + myCar.getNumberOfWheels());
        System.out.println("max Speed: " + myCar.getMaxSpeed());
        myVehicle.setMaxSpeed(150);
        System.out.println("max Speed: " + myCar.getMaxSpeed());
    }
}
```

```java
public class Vehicle {
    protected int numberOfWheels;
    protected int maxSpeed;

    public Vehicle() {
        System.out.println("## in default constructor of Vehicle");
        this.numberOfWheels = 4;
        this.maxSpeed = 100;
    }

    public Vehicle(int numberOfWheels, int maxSpeed) {
        System.out.println("## in constructor of Vehicle");
        this.numberOfWheels = numberOfWheels;
        this.maxSpeed = maxSpeed;
    }

    public int getNumberOfWheels() {
        return this.numberOfWheels;
    }

    public int getMaxSpeed() {
        return this.maxSpeed;
    }

    public String printMaxSpeed() {
        return this.maxSpeed + " km/h";
    }

    public void setMaxSpeed(int newMaxSpeed) {
        if (newMaxSpeed < 0) {
            return;
        }
        this.maxSpeed = newMaxSpeed;
    }

}
```

```java
public class Car extends Vehicle {
    private String color;

    public Car(String color) {
        super(4, 200); // always needs to be the first statement
        System.out.println("## in constructor of Car");
        this.color = color;
    }

    @Override
    public void setMaxSpeed(int newMaxSpeed) {
        if (newMaxSpeed < 1000) {
            System.out.println("No car shall be this slow tbh");
            return;
        }
        this.maxSpeed = newMaxSpeed;
    }
}
```

```java
public class Car extends Vehicle {
    private String color;

    public Car(String color) {
        super(4, 200); // always needs to be the first statement
        System.out.println("## in constructor of Car");
        this.color = color;
    }

    @Override
    public void setMaxSpeed(int newMaxSpeed) {
        if (newMaxSpeed < 1000) {
            System.out.println("No car shall be this slow tbh");
            return;
        }
        this.maxSpeed = newMaxSpeed;
    }
}
```

```java
public class Truck extends Vehicle {
    private boolean isFireTruck;
    private final String hornSound;

    public Truck(boolean isFireTruck) {
        super(4, 200); // always needs to be the first statement
        System.out.println("## in constructor of Truck");
        this.isFireTruck = isFireTruck;
        this.hornSound = "test";
    }

    public boolean getIsFireTruck() {
        return this.isFireTruck;
    }
}
```

## #3 `static` in einer Klasse

**Lernziele:**
* statische und dynamische Variablen
* statische und dynamische Methoden

```java
// main.java
public class Main {
    public static void main(String[] args) {
        Counter.printCounterStatic("Static");
        Counter.increaseCounterStatic();
        Counter.printCounterStatic("Static");

        Counter myCounter = new Counter();
        Counter.increaseCounterStatic();
        myCounter.increaseCounterDynamic();
        myCounter.printCounterDynamic("Dynamic");
    }
}
```

```java
public class Counter {
    static int counterValueStatic = 0;
    int counterValueDynamic = 0;

    public static void increaseCounterStatic() {
        counterValueStatic++;
    }

    public void increaseCounterDynamic() {
        this.counterValueDynamic++;
    }

    public void printCounterDynamic(String classID) {
        System.out.println(">> execute printCounterDynamic of class " + classID);
        System.out.println("static: " + counterValueStatic);
        System.out.println("dynamic: " + this.counterValueDynamic);
    }

    public static void printCounterStatic(String classID) {
        System.out.println(">> execute printCounterStatic of class " + classID);
        System.out.println("dynamic: " + counterValueStatic);
    }
}
```