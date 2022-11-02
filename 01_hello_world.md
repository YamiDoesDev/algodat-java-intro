# 01: Hello World

## Approach 1: Simple String Output

```java
// main.java
public class main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
```shell
>> javac main.java
>> java main 
Hello, World!
```

Was sagt dieser Code nun aus?
* Eine Klasse "main" ist öffentlich
* Dem Compiler wird die statische Methode `main` vorlegt 
  * Diese wird bei jedem Java Code genutzt
* Wir rufen die Klasse System auf und führen einen `println`-Befehl aus
* `Hello, World!` wird in der Konsole ausgegeben



## Approach 2: Using Console Arguments

```java
// main.java
public class main {
    public static void main(String[] args) {
        System.out.println(args[0] + " " + args[1]);
    }
}
```
```shell
>> javac main.java
>> java main Hello, World!
Hello, World!
```

Was ist nun anders?
* Die Main-Methode übergibt standardmäßig Konsolenargumente als Array vom Typ String mit dem Namen `args`
* Jedes Argument hat einen Index im Array
* Für 2 Argumente rufen wir die ersten zwei Indexes auf, beginnend bei `0`

