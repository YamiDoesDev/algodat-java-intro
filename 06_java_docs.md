# 06: JavaDoc

Quelle: [JavaDoc Cheatsheet](https://binfalse.de/2015/10/05/javadoc-cheats-sheet/)

Output as PDF: [JavaDoc from class Main](https://github.com/YamiDoesDev/algodat-java-intro/blob/main/media/javadoc_main.pdf)

```java
/**
 * This is the Main class
 * @version 1.0.1
 * @author Justin Drtvic
 */
// Main.java
public class Main {
    /**
     * this is the main function, which is needed to execute the code
     * @param args params passed by the command line
     */
    public static void main(String[] args) {
        System.out.println( addition(1,2) );
    }

    /**
     * addition of two integer numbers
     * @param left number for left side
     * @param right number for right side
     * @return sum of two numbers
     * @throws IllegalArgumentException for numbers smaller than 0
     * @see Math
     * @see <a href="https://www.mathebibel.de/addition/">Mathebibel Addition</a>
     * @since Java API 7
     * @deprecated deprecated since 3.0.0
     */
    public static int addition(int left, int right) {
        if (left < 0 || right < 0) {
            throw new IllegalArgumentException("we don't like numbers smaller than 0");
        }
        return left + right;
    }
}
```