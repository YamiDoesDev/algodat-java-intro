# 05: Typen von Objekten

## Enumerations

```java
// SecurityLevel.java
public enum SecurityLevel {
    LOW,
    MEDIUM,
    HIGH;
}
```

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        SecurityLevel networkSecurity = SecurityLevel.MEDIUM;

        // comparing enum items
        System.out.println(networkSecurity == SecurityLevel.HIGH); // false
        System.out.println(networkSecurity.compareTo(SecurityLevel.LOW)); // 1
        System.out.println(networkSecurity.compareTo(SecurityLevel.MEDIUM)); // 0
        System.out.println(networkSecurity.compareTo(SecurityLevel.HIGH)); // -1

        // print all possible values
        for(SecurityLevel value : SecurityLevel.values()) {
            System.out.println(value.ordinal() + " " + value.name() + " " + value);
        }

        switch (networkSecurity) {
            case LOW:
                System.out.println("The network security MUST be increased!");
                break;
            case MEDIUM:
                System.out.println("The network security needs improvements");
                break;
            case HIGH:
                System.out.println("The network security is good so far");
                break;
        }
    }
}
```

## Generics

```java
// Main.java
public class Main /*extends Language implements Regex*/ {
    public static void main(String[] args) {

        SaveState<String> stateFirst = new SaveState<String>("Begin of the story");
        SaveState<String> stateSecond = new SaveState<String>("Near last boss fight");

        System.out.println(stateFirst);
        System.out.println(stateSecond);

        System.out.println("second state bigger? " + stateSecond.compareTo(stateFirst));
        System.out.println("first state bigger? " + stateFirst.compareTo(stateSecond));

        stateFirst.setSaveState("Finished tutorial");
        System.out.println(stateFirst.getSaveState());
    }
}
```

```java
// SaveState.java

import java.security.InvalidParameterException;

public class SaveState<T> implements Comparable<SaveState> {
private T saveEntry;
private int saveID = 0;
private static int staticSaveID;

    // constructor
    SaveState(T saveEntry) throws InvalidParameterException {
        if(saveEntry == null) throw new InvalidParameterException("entry shall not be null");
        this.saveEntry = saveEntry;
        this.saveID = staticSaveID;
        staticSaveID++;
    }

    public int getSaveID() {
        return this.saveID;
    }

    public T getSaveState() {
        return this.saveEntry;
    }

    public void setSaveState(T saveEntry) throws InvalidParameterException {
        if(saveEntry == null) throw new InvalidParameterException("entry shall not be null");
        this.saveEntry = saveEntry;
    }

    @Override
    public String toString() {
        try {
            return this.saveID + ": " + this.saveEntry.toString();
        } catch (Exception exception) {
            System.out.println("T.toString() for Class " + saveEntry.getClass() + " does not exist");
            return null;
        }
    }

    @Override
    public int compareTo(SaveState object) {
        if (this.saveID > object.getSaveID()) {
            return 1;
        }
        if (this.saveID < object.getSaveID()) {
            return -1;
        }
        return 0;
    }
}
```

### Abstract and Interface
```java
// Regex.java
public interface Regex {
    public String concatStrings(String left, String right);
}
```
```java
// Main.java
abstract class Language {
    public void showLanguage() {
        System.out.println("This text is presented to you by Java");
    }
    public abstract void sayHelloWorld();
}

// Main.java
public class Main extends Language implements Regex {
    public static void main(String[] args) {
        // Language myLanguage = new Language();
        // 'Language' is abstract; cannot be instantiated

        Main myObject = new Main();
        myObject.sayHelloWorld();

        String wortwitz = myObject.concatStrings("du", "schlampe");
        System.out.println(wortwitz); // duschlampe
    }

    @Override
    public void sayHelloWorld() {
        System.out.println("I refuse to say that!");
    }

    @Override
    public String concatStrings(String left, String right) {
        return left + right;
    }
}
```

## Collections

```java
import java.util.*;

// Main.java
public class Main {
    public static void main(String[] args) {

        String[] alphabet = {
                "bee",
                "apple",
                "clown"
        };
        System.out.println( Arrays.toString(alphabet) );

        ArrayList<String> myArrayList = new ArrayList<String>();
        TreeSet<String> myTreeSet = new TreeSet<String>();
        HashMap<Integer, String> myHashMap = new HashMap<>();

        for(String selection: alphabet) {
            myArrayList.add(selection);
            myTreeSet.add(selection);
            myHashMap.put(myHashMap.size(), selection);
        }

        Set<Integer> mapKeys = myHashMap.keySet();
        System.out.println(mapKeys);

        Collection<String> mapValues = myHashMap.values();
        System.out.println(mapValues);

        Iterator<String> arrayListIterator = myArrayList.iterator();
        Iterator<String> treeSetIterator = myTreeSet.iterator();
        Iterator<String> hashMapIterator = myHashMap.values().iterator();

        System.out.println("--- arrayList ---");
        for (String selectedValue: myArrayList) {
            System.out.println(selectedValue);
        }
        System.out.println("--- arrayListIterator ---");
        while (arrayListIterator.hasNext()) {
            System.out.println(arrayListIterator.next());
        }

        System.out.println("--- treeSet ---");
        for (String selectedValue: myTreeSet) {
            ystem.out.println(selectedValue);
        }
        System.out.println("--- treeSetIterator ---");
        while (treeSetIterator.hasNext()) {
            System.out.println(treeSetIterator.next());
        }

        System.out.println("--- hashMap ---");
        for (Map.Entry<Integer, String> pair : myHashMap.entrySet()) {
            System.out.println(pair.getKey() + ": " + pair.getValue());
        }
        System.out.println("--- hashMapIterator ---");
        while (hashMapIterator.hasNext()) {
            System.out.println(hashMapIterator.next());
        }
    }
}
```

* List - f??r beliebig gro??e Listen, deren Elemente auch ??ber einen Index zugegriffen werden k??nnen,
    * `ArrayList` - Indizierte Liste, deren Gr????e dynamisch ver??ndert werden kann. Indexzugriffe sind schnell, Gr????en??nderungen sind aufw??ndig.
    * `LinkedList` - Verkettete Liste. Indexzugriffe sind langsam, Einf??gen und L??schen ist schnell.
* Set - zur Darstellung von Mengen
    * `HashSet` - ungeordnete Datenmenge (ohne Duplikate)
    * `TreeSet` - Sortierte Menge.
* Map - f??r Paare von Daten verschiedenen Typs.
    * `HashMap` - Menge von (Schl??ssel,Wert)-Paaren
    * `TreeMap` - nach Schl??sseln sortierte Menge von (Schl??ssel,Wert)-Paaren

### Collection Interface (List, Set, Map)

| Methode                         | Beschreibung                                                  |
|---------------------------------|---------------------------------------------------------------|
| int size()                      | liefert die Anzahl der Eintr??ge                               |
| boolean isEmpty()               | pr??ft, ob keine Eintr??ge vorhanden sind                       |
| boolean contains(Object o)      | pr??ft, ob o eingetragen ist                                   |
| boolean add(Object o)           | pr??ft, ob alle Elemente aus c enthalten sind                  |
| boolean addAll(Collection c)    | tr??gt alle Elemente aus c ein (optional)                      |
| boolean remove(Object o)        | entfernt o (optional)                                         |
| boolean removeAll(Collection c) | entfernt die in c angegebenen Elemente (optional)             |
| boolean retainAll(Collection c) | entfernt alle Elemente, au??er die in c angegebenen (optional) |
| boolean equals(Object o)        | pr??ft, ob o mit der Collection ??bereinstimmt                  |
| Iterator iterator()             | erzeugt einen Iterator                                        |
| void clear()                    | entfernt alle Elemente (optional)                             |

### List Interface

| Methode               | Beschreibung                                             |
|-----------------------|----------------------------------------------------------|
| Object get(int i)     | liefert das Element an Position i (ohne es zu entfernen) |
| int indexOf(Object o) | liefert den Index des ersten Vorkommens von o oder -1    |

### Map Interface

| Methode                              | Beschreibung                                              |
|--------------------------------------|-----------------------------------------------------------|
| boolean containsKey(Object key)      | pr??ft, ob ein Datenpaar mit Schl??ssel key eingetragen ist |
| boolean containsValue(Object value)  | pr??ft, ob ein Datenpaar mit Wert value eingetragen ist    |
| Object get(Object key)               | liefert den eingetragenen Wert zum Schl??ssen key          |
| Object put(Object key, Object value) | tr??gt das Datenpaar(key,value) ein (optional)             |
| boolean remove(Object key)           | entfernt das Datenpaar mit Schl??ssel key (optional)       |

### Iteratoren (List, Set)

| Methode           | Beschreibung                                    |
|-------------------|-------------------------------------------------|
| boolean hasNext() | pr??ft, ob ein weiteres Element existiert        |
| Object next()     | liefert das n??chste Element und schaltet weiter |
| void remove()     | l??scht das aktuelle Element                     |

### ListIterator (List)

| Methode               | Beschreibung                                              |
|-----------------------|-----------------------------------------------------------|
| boolean hasPrevious() | pr??ft, ob ein Vorg??nger existiert                         |
| Object previous()     | liefert das vorherige Element                             |
| void add(Object o)    | f??gt ein neues Element o hinter dem aktuellen Element ein |
| void set(Object o)    | ersetzt das aktuelle Element durch o                      |