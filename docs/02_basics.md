# 02: Basics

## Table of Contents
1. [Nutzung der Konsole](#nutzung-der-konsole)
2. [Primitive Datentypen](#primitive-datentypen)
3. [Nicht Primitive Datentypen](#)
4. [Operatoren](#)
5. [Bedingungen](#)
6. [Schleifen](#)
7. [Exceptions](#exceptions)

## Nutzung der Konsole

### Ausgabe
```java

System.out.println("print me and create a new line");
System.out.println(); // prints nothing but creates new line afterwards
        
System.out.print("print me without a new line | ");
System.out.print("print me but add a new line \n");
System.out.print("yeah, this is on the new line! \n");
System.out.println(); // prints nothing but creates new line afterwards

// https://www.digitalocean.com/community/tutorials/java-printf-method
System.out.printf("%s %s \n", "parameter 1", "parameter 2");
System.out.printf("%s %e %f", "10.50", 10.50, 10.50);
```

### Eingabe
```java
import java.util.Scanner;

// class and method : start
Scanner myScanner = new Scanner(System.in);
System.out.print("Enter Username: ");
String username = myScanner.nextLine();
System.out.print("Enter Password: ");
String password = myScanner.nextLine();
System.out.println("your Username: " + username + "\nyour password: " + password );
// class and method : end
```

## Primitive Datentypen

Quelle: [w3schools.com](https://www.w3schools.com/java/java_data_types.asp)

| Data Type | Size | Description |                                                                        
|-----------|---------|-------------------------------------------------------------------------------------|
| byte      | 1 byte  | Stores whole numbers from -128 to 127                                               |
| short     | 2 bytes | Stores whole numbers from -32,768 to 32,767                                         |
| int       | 4 bytes | Stores whole numbers from -2,147,483,648 to 2,147,483,647                           |
| long      | 8 bytes | Stores whole numbers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807   |
| float     | 4 bytes | Stores fractional numbers. Sufficient for storing 6 to 7 decimal digits             |
| double    | 8 bytes | Stores fractional numbers. Sufficient for storing 15 decimal digits                 |
| boolean   | 1 bit   | Stores true or false values                                                         |
| char      | 2 bytes | Stores a single character/letter or ASCII values                                    |

### Type Casting

Bei Type Casting handelt es sich um das überführen eines primitiven Datentypen 
in einen anderen.

Quelle: [w3schools.com](https://www.w3schools.com/java/java_type_casting.asp)

#### Widening Casting (automatically)

Hier wird ein kleinerer Typ in einen größeren Typ konvertiert

`byte` -> `short` -> `char` -> `int` -> `long` -> `float` -> `double`

```java
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double

System.out.println(myInt);      // Outputs 9
System.out.println(myDouble);   // Outputs 9.0
```

#### Narrowing Casting (manually)

Hier wird ein größerer Typ in einen kleineren Typ konvertiert

`double` -> `float` -> `long` -> `int` -> `char` -> `short` -> `byte`

```java
double myDouble = 9.78d;
int myInt = (int) myDouble; // Manual casting: double to int

System.out.println(myDouble);   // Outputs 9.78
System.out.println(myInt);      // Outputs 9
```

## Nicht Primitive Datentypen

### String

String ist eine Wrapperklasse, welche eine Zeichenkette aus einzelnen chars 
zusammenbaut. In manchen Programmiersprachen (z.B. C++) ist ein String 
vergleichbar mit einem char-Array.

```java
String myString = "this is a text";
System.out.println("myString: " + myString);

String concatString = "hello" + "World";
System.out.println("concatString: " + concatString);
```

Methoden der Standardbibliothek:
```java
myString.charAt(); // Returns the char value at the specified index.
myString.indexOf(); // Returns the index within this string of the first occurrence of the specified substring.
myString.substring(); // Returns a string that is a substring of this string.
myString.equals(); // Compares this string to the specified object.
myString.toLowerCase(); // Converts all of the characters in this String to lower case.
myString.toUpperCase(); // Converts all of the characters in this String to upper case.
myString.contains(); // Returns true if and only if this string contains the specified sequence of char values.
myString.replaceAll(); // Replaces each substring of this string that matches the given regular expression with the given replacement.
myString.compareTo(); // Compares two strings lexicographically. The comparison is based on the Unicode value of each character in the strings.
```

### Numeric Datatypes

Im Gegensatz zu den primitiven Datentypen werden hier "Wrapper" verwendet, um
dynamisch mit den Werten arbeiten zu können. Das erlaubt auch die Erweiterung
um verschiedene Methoden in der Standardbibliothek.

Integer:
```java
Integer myNumber = 10;
Integer.parseInt(); // Parses the string argument as a signed decimal integer.
Integer.parseUnsignedInt(); // Parses the string argument as an unsigned decimal integer.
Integer.valueOf(); // Returns an Integer object holding the value of the specified String.
```

Float and Double:
```java
Double myDouble = 10.0;
myDouble.isNaN(); // Returns true if this Double value is a Not-a-Number (NaN), false otherwise.

Float myFloat = (float)10.0;
myFloat.isNaN(); // Returns true if this Float value is a Not-a-Number (NaN), false otherwise
```

Funktionen für alle Numerischen Datentypen (Nicht Primitiv):
```java
myNumber.compareTo(); // Compares two Integer objects numerically.
myNumber.toString(); // Returns a String object representing this Integer's value.
myNumber.intValue(); // Returns the value of this Integer as an int.
myNumber.floatValue(); // Returns the value of this Integer as a float after a widening primitive conversion.
myNumber.doubleValue(); // Returns the value of this Integer as a double after a widening primitive conversion.
myNumber.shortValue(); // Returns the value of this Integer as a short after a narrowing primitive conversion.
```

### Arrays
Bei Arrays handelt es sich um Schleifen eines bestimmten Datentypen. Sie werden
verwendet, um mehrere Werte in einer Variable zu speichern.

```java
String[] myStringArray = new String[3];
myStringArray[0] = "ROT";
myStringArray[1] = "GRÜN";
myStringArray[2] = "BLAU";

int[] myIntArray = {0,1,2};

System.out.println(myIntArray.length); // 3
System.out.println(Arrays.toString(myIntArray)); // [0,1,2]
```

multidimensionale Arrays:
```java
int[][] my2DArray = {
        {1, 2},
        {3, 4, 5},
        {6, 7, 8, 9},
};

System.out.println(my2DArray.length);
System.out.println(my2DArray[0].length);

for(int row = 0; row < my2DArray.length; row++) {
    System.out.print("[");
    for(int column = 0; column < my2DArray[row].length; column++) {
        if (column == (my2DArray[row].length - 1) ) {
            System.out.print(my2DArray[row][column]);
            continue;
        }
        System.out.print(my2DArray[row][column] + ", ");
    }
    System.out.println("]");
}
```

Methoden:
```java
Arrays.toString(myArray); // a string representation of the object.
Arrays.copyOf(myArray, 3); // Copies the specified array, truncating or padding with zeros (if necessary) so the copy has the specified length.
Arrays.compare(myArray, myArray); // Compares two int arrays lexicographically.
Arrays.equals(myArray, myArray); // Returns true if the two specified arrays of ints are equal to one another.
Arrays.sort(myArray); // Sorts the specified array into ascending numerical order
Arrays.fill(myArray, 0); // Assigns the specified int value to each element of the specified array of ints.
```

## Operatoren

### Arithmetic Operators
```java
int calcAddition = 20 + 10; // = 30
int calcSubstraction = 20 - 10; // = 10
int calcMultiplication = 20 * 10; // = 200
int calcDivision = 20 / 10; // = 2
int calcModulus = 20 % 3; // = 2

int myNumber = 10;
myNumber++; // myNumber = 11
myNumber--; // myNumber = 10
myNumber--; // myNumber = 9
```

### Comparison Operators
```java
int biggerNumber = 20;
int biggerNumberAgain = 20;
int smallerNumber = 10;

// (20 == 20) => true
// (20 != 20) => false
// (20 > 10) => true
// (20 < 10) => false
// (20 >= 10) => true
// (20 >= 10) => true
```

## Bedingungen

wir verwenden folgende Variablen:
```java
int biggerNumber = 20;
int biggerNumberAgain = 20;
int smallerNumber = 10;
```

### if-condition (better version)
```java
if (biggerNumber > smallerNumber) {
    System.out.println("the left number is bigger!");
}
```

### if-condition (worse version)
```java
// prefer to not write it down like this!
if (biggerNumber == biggerNumberAgain) 
    System.out.println("We don't do this here...");
```

### if-else-condition
```java
if (biggerNumber < smallerNumber) {
    System.out.println("the left number is smaller!");
} else if (biggerNumber < biggerNumberAgain) {
    System.out.println("but this time, the left number is smaller!");
} else {
    System.out.println("the left number is just too big!");
}
```

### switch-case
```java
int luckyNumber = 69;
switch (luckyNumber) {
    case 13:
        System.out.println("some people consider 13 to be a lucky number");
        break; // we need this to avoid default!
    case 7:
        System.out.println("slot machines value this number high");
        break; // we need this to avoid default!
    default:
        System.out.println("seems, your number was not lucky enough...");
}
```

## Schleifen

### while-loop
```java
int whileNumber = 3;
while (whileNumber > 0) {
    System.out.println(whileNumber);
    whileNumber --;
}
```

### do-while-loop
```java
System.out.println("--- doWhileNumber:");
int doWhileNumber = 3;
do {
    System.out.println(doWhileNumber);
    doWhileNumber--;
} while(doWhileNumber > 0);
```

### for-loop
```java
System.out.println("--- forNumber:");
for(int iterator = 0; iterator <= 5; iterator++) {
    System.out.println(iterator);
}
```

### Beispiel Ausführung
```java
int myNumber = 1;
// count, how many times we can add 2 until we reach 16,
// but we pretend, 13 doesn't exist for reasons
for(int counter = 0; counter <= 10; counter++) {
    myNumber += 2;
    if (myNumber == 13) {
        continue;
    }
    System.out.println(counter);
    if (myNumber >= 16) {
        break;
    }
}
```

### Hinweis
Vermeidet einfache Variablennamen wie i, u, usw.m um die Lesbarkeit einfach zu halten
```java
// 
for(int i = 0; i < 10; i++) {
    for(int u = 30; i > 15; u++) {
        myArray[u][i] = i + u;
    }
}
```

### for-each-loop

#### arrays
```java
int[] myArray = {1, 2, 3};
        
for(int selectedValue: myArray) {
    System.out.println("myArray: " + selectedValue);
    selectedValue = 0;
}

System.out.println(Arrays.toString(myArray));

for(int selection: myArray) {
    System.out.println(selection);
}
```

#### lists
```java
LinkedList<String> myLinkedList = new LinkedList<>();
myLinkedList.add("List_1");
myLinkedList.add("List_2");
myLinkedList.add("List_3");

for(int selectedValue: myArray) {
    System.out.println(selectedValue);
}
```

### maps

```java
HashMap<Integer, String> myHashMap = new HashMap<>();
myHashMap.put(1, "Larry");
myHashMap.put(2, "Steve");
myHashMap.put(3, "James");

myHashMap.forEach((key, value) -> {
    System.out.println(key + " " + value);
});
```

## Exceptions

```java
public class Main {
    public static void main(String[] args) {

        // simple exception handling
        try {
            int[] myNumbers = {1, 2, 3};
            System.out.println(myNumbers[10]);
        } catch (Exception exception) {
            System.out.println(exception);
            System.out.println("---");
        }

        // extended exception handling
        try {
            int[] myNumbers = {1, 2, 3};
            printTenthIndex(myNumbers);
        } catch (RuntimeException exception) {
            System.out.println("class: " + exception.getClass()); // class: class java.lang.RuntimeException
            System.out.println("cause: " + exception.getCause()); // cause: java.lang.RuntimeException: array is not big enough
            System.out.println("message: " + exception.getMessage()); // message: index was not found
        } finally {
            System.out.println("finally! The 'try catch' is finished.");
        }
    }

    public static void printTenthIndex(int[] array) throws RuntimeException {
        Exception r = new RuntimeException("array is not big enough"); // not every exception supports causes
        if (array.length < 11) {
            throw new RuntimeException("index was not found", r);
        }
        System.out.println(array[10]);
    }
}
```