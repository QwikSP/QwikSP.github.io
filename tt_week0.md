---
layout: page
title: Week 0 notes
subtitle: Week 0
---
[Run Time](https://replit.com/github/QwikSP/DataStructures)

A data structure is a method of organizing data. Think of a variable holding a single integer value(ex: int n=4;) or sequences of numbers(ex: int[] numbers=new int[]{ 1,2,3 };) or tables of data, or databases: these are all well-defined data structures. Data Structures and organizing data will require students to become more algorithmic in coding.

Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.

Examples of objects
- dictionaries
- hashmaps 
- linked lists


- Hashmap used in order to call main file of the corresponding file
- polymorhism used so that the main file can be called over and over again but with different files being called

## Menu
```java
public class main2 {
    String title;
    Runnable action;

    public main2(String title, Runnable action) {
        this.title = title;
        this.action = action;
    }

    public String getTitle() {
        return this.title;
    }

    public Runnable getAction() {
        return this.action;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        //hash map to store values

        Map<Integer, main2> main2 = new HashMap<>();

        //putting values into a hashmap
        
        main2.put(1, new main2("Matrix", () -> Matrix.main(null)));
        main2.put(2, new main2("IntByReference", () -> IntByReference.main(null)));

        //printing out console for the user for easy viewing
        
        System.out.println("main2:");
        for (Map.Entry<Integer, main2> pair : main2.entrySet()) {
            System.out.println(pair.getKey() + " ==> " + pair.getValue().getTitle());
        }
        Boolean temp = true;
        while (temp = true) {
            try {
                int input = sc.nextInt();
                main2 m = main2.get(input);
                m.getAction().run();
            } catch (Exception e) {
                System.out.println("Exiting...");
                return;
            }
        }
    }

}




```


## IntByReference
```java
package com.example.sping_portfolio.controllers;

public class IntByReference {
        private int value;

        // Hack: create IntByReference, swapToLowHighOrder and toString methods
        public IntByReference(int value){
            this.value = value;
        }
        // static method that enables me to see numbers swapped by reference (before, after)
        public int getValue(){
            return value;
        }

        public void setValue(int v){
            value = v;
        }

        public void swapToLowHighOrder(IntByReference b){
            //object a has b value
            if (value > b.getValue()){
                int temp = value;
                value = b.getValue();
                b.setValue(temp);
            }

        }

    public String toString(){
            return ""+value;
    }

        public static void swapper(int n0, int n1) {
            IntByReference a = new IntByReference(n0);
            IntByReference b = new IntByReference(n1);
            System.out.println("Before: " + a + " " + b);
            a.swapToLowHighOrder(b);  // conditionally build swap method to change values of a, b
            System.out.println("After: " + a + " " + b);
            System.out.println();
        }

        // static main method that provides some simple test cases
        public static void main(String[] ags) {
            IntByReference.swapper(21, 16);
            IntByReference.swapper(16, 21);
            IntByReference.swapper(16, -1);
        }

}
```



## Matrix
```java
package com.example.sping_portfolio.controllers;

public class Matrix {
    private final int[][] matrix;

    // store matrix
    public Matrix(int[][] matrix) {
        this.matrix = matrix;
    }

    // Hack: create toString method using nested for loops to format output of a matrix


    public String toString(){
        String matrixS = "";
        for(int i=0; i < matrix.length; i++){
            for(int j=0; j < matrix[i].length; j++){
                if (matrix[i][j] == -1){
                    matrixS += "  ";
                }
                else {
                    matrixS += Integer.toHexString(matrix[i][j]) + " ";
                }

            }
            matrixS += "\n";
        }

        String matrixB = "";

        for(int i=0; i < matrix.length; i++){
            for(int j=0; j < matrix[i].length; j++){
                if (matrix[i][j] == -1){
                    matrixB = "  " + matrixB;
                }
                else {
                    matrixB = Integer.toHexString(matrix[i][j]) + " " + matrixB;
                }

            }
            matrixB = "\n" + matrixB;
        }
//        for (int i = matrixS.length()-1; i >= 0; i--){
//                matrixB += matrixS.charAt(i);
//        }
        matrixS = matrixS + matrixB;
        return(matrixS);
    }

    // declare and initialize a matrix for a keypad
    static int[][] keypad() {
        return new int[][]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 }, {-1, 0, -1} };
    }

    // declare and initialize a random length arrays
    static int[][] numbers() {
        return new int[][]{ { 0, 1 },
                { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 },
                { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15 } };
    }

    // tester method for matrix formatting
    public static void main(String[] args) {
        Matrix m0 = new Matrix(keypad());
        System.out.println("Keypad:");
        System.out.println(m0);

        Matrix m1 = new Matrix(numbers());
        System.out.println("Numbers Systems:");
        System.out.println(m1);
    }

}
```