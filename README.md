# Java-Coding-Convention

*Java Coding Convention summarized by me.*

## File Organization

*Files should not be longer than 2000 lines.*

*Each Java source file contains a single public class/interface and associated private classes/interfaces. The public class/interface should be the first one displayed.*

## Source ordering

1. Beginning comments

    ```java
    /*
     * Classname
     *
     * Version Info
     *
     * Copyright notice
     */
    ```
2. Package and Import statements
    ```java
    package java.awt;
    import java.awt.peer.CanvasPeer;
    ```
3. Class/interface declarations

    * Class/interface documentation comment

        [How to Write Doc Comments for Javadoc](http://java.sun.com/products/jdk/javadoc/writingdoccomments.html)

        [javadoc Homepage](http://java.sun.com/products/jdk/javadoc/)

        ```java
        /**
         * Class/interface description goes here
         *
         * @version 1.0
         * @author Myhq
         */
        ```
    * Class/interface statement
        ```java
        public class Blah extends SomeClass {

        public interface GroupedInterface extends Interface1, Interface2, Interface3 {
        ```
    * Class/interface implementation comment, if neccessary (class-wide/interface-wide information that was not appropriate for the documentation comment
        ```java
        /*
         * A class implementation
         * comment can go here.
         */
        ```
    * **static** variables, *public* then *protected* and *privated*
        ```java
        /** classVar1 documentation comment */
        public static final int classVar1;
        /** classVar2 documentation comment */
        protected static final int classVar2;
        /** classVar3 documentation comment */
        privated static final int classVar3;
        ```
    * Instance varables, *public* then *protected* and *privated*
        ```java
        /** insVar1 documentation comment */
        public int insVar1;
        /** insVar2 documentation comment */
        protected int insVar2;
        /** insVar3 documentation comment */
        privated int insVar3;
        ```
    * Contructors
        ```java
        /**
         * Constructor1 documentation comments
         */
        public Blah() {
            // Constructor1
        }

        /**
         * Constructor2 documentation comments
         *
         * @param mode description-of-mode
         */
        public Blah(int mode) {
            // Constructor2
        }
        ```
    * Methods, should be grouped by functionality
        ```java
        /**
         * doSomething method documentation comments
         */
        public doSomething() {
        }

        /**
         * doSomething method documentation comments
         *
         * @param mode description-of-mode
         */
        public doSomethingElse(int mode) {
        }
        ```

## Indentation

*4 spaces should be used as the unit of indentation.*

* Line length: *depends on project, usually 80/100/120.*

* Wrapping line
    1. Break after a comma
        ```java
        functionA(longExp1, longExp2,
                longExp3, longExp4);
        ```
    2. Break before an operator
        ```java
        exp1 = longExp1 + longExp2
            + longExp3 + longExp4;
        ```
    3. Prefer higher-level break to lowe-level break
    4. Align the new line with the beginning of the expression at the same level on the previous line
        ```java
        exp1 = longExp1 * (longExp2 + longExp3 + anotherLongExp)
            + longExp4 + longExp5; // Prefer

        exp2 = longExp1 * (longExp2 + longExp3
                        + anotherLongExp) + longExp4 + longExp5; // Avoid
        ```
    5. If the above rules suck, just indent 8 spaces instead
        ```java
        private static synchronized fuckingLongMethodName(int arg1,
                int arg2, int andStillAnotherArg) {

        }
        ```
    6. Use 8 spaces for wrapping *if* condition
        ```java
        if ((cond1 || cond2)
                || (cond3 && cond4)
                || !suck() {
            doSomething();
        }
        ```
    7. Ternary expressions
        ```java
        alpha = (alongBooleanExpression) ? beta : gamma;

        alpha = (alongBooleanExpression) ? beta
                                        : gamma;

        alpha = (alongBooleanExpression)
                ? beta
                : gamma;
        ```

## Declaration

* One declaration per line
    ```java
    int mode; // Execute mode
    int size; // Size of table
    ```
* Put declarations only at the beginning of blocks
    ```java
    void method() {
        int int1;           // beginning of method block
        if (cond) {
            int int2;       // beginning of if block
        }
    }
    ```
* Avoid local declaration that hide declarations at higher levels
    ```java
    void method() {
        int int1;
        if (cond) {
            int int1;       // avoid!
        }
    }
    ```
* Try to initialize local variables where they're declared
    ```java
    int iVar1 = 0;
    ```
* Class/Interface declarations:
    * No space between a method name and "("
    * "{" appears at the end of the same line as the declaration statement
    * "}" starts a line by itself, except when the method is a null one, it should appear immediately after "{"
    ```java
    void method1() {}

    void method2() {
        int int1;
        if (cond) {
            int int2;
        }
    }
    ```
## Statements

* Each line should contain at most one statement
    ```java
    a++; b++;   // avoid!
    ```
* *if* Statement
    ```java
    if (cond1) {
        // statements
    } else if (cond2) {
        // statements
    } else (cond3) {
        // statements
    }
    ```
* *for* Statement
    ```java
    for (initialization, condition, update) {
        // statements
    }
    ```
* *while* Statement
    ```java
    while (cond) {
        // statements
    }

    do {
        // statements
    } while (condition);
    ```
* *switch* Statement
    ```java
    switch (cond) {
        case A:
            // statements
            break;      // should break after a case
        case B:
            // statements
            break;
        default:
            // statements
            break;      // should break after a case
    }
    ```
* *try-catch* Statement
    ```java
    try {
        // statements
    } catch (Exception e) {
        // statements
    }
    ```

## White Spaces

* Two blank lines
  * Between sections of a source file
  * Between class and interface definitions
* One blank lines
  * Between methods
  * Between the local variables in a method and its first statement
  * Before a block or a single-line comment
  * Between logical sections inside a method to improve readability

## Blank Spaces

* A keyword followed by a parenthesises, not between method name and its open parenthesis, to distinguish keywords from method calls
    ```java
    while (true) {

    }
    ```
* After commas in argument lists
    ```java
    public void doSomething(int arg1, Object arg2) {

    }
    ```
* The operands of all binary operators except ".". There's no space between unary operator and its operand
    ```java
    a = b + c;
    d++;
    ```
* The expressions in a for statement
    ```java
    for (initial; condition; update) {

    }
    ```
* After casts
    ```java
    double a;
    int b;
    a = (double) b;
    ```

## Naming Conventions

* Class/Interface should be nouns, uppered-case first letter, simple, descriptive. Avoid acronyms and abbreviations unless they're widely known.
* Method should be verbs, camelCase.
* Variable should be camelCase, one character variable should be avoid except for temporary.
* Constants should be UPPERCASE_WITH_UNDERSCORE;

## Programming Practices

* Ensure encapsulation by providing accessors.
* Avoid using an object instance to access a *static* variable/method. Use class name instead.
* Literals (numerical constants) should not be coded directly, except for -1/0/1, which can appear in a *for* loop as counter values.
* Avoid assigning serveral variables to the same value in a single statement.
    ```java
    a = b = 10;     // avoid!
    ```
* Do not use the assignment operator in a place where it can be easily confused with the equality operator
    ```java
    if (c++ = d++) {         // avoid, Java disallows
    }

    if ((c++ = d++) != 0) {         // OK
    }
    ```
* Do not use embedded assignment
    ```java
    d = (a = b + c) + r;    // avoid!
    a = b + c;
    d = a + r;
    ```
* Use parentheses in expressions involving mixed operators to avoid operator precedence problems
    ```java
    if (a == b && c == d) { // avoid!

    }
    if ((a == b) && (c == d) { // OK

    }
    ```
* Try to make the structure of your program match the intent
    ```java
    // Avoid!
    if (booleanExp) {
        return true;
    } else {
        return false;
    }

    // Better alternative
    return booleanExp;
    // Avoid!
    if (cond) {
        return x;
    }
    return y;

    // Better alternative
    return (cond ? x : y);
    ```
* If an expression containing a binary operator appears before the "?" in the ternary "?:" operator, it should be parenthesized
    ```java
    (x >= 0) ? x : -x;
    ```