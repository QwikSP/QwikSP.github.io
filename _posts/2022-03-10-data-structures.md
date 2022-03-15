---
layout: post
title: Data Structures Work!
subtitle: my work related to data structures
---
[Run Time](https://replit.com/@Qwiks/CSATri3#Main.java)

## GitHub Links
1. [Menu](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/main2.java)
2. [IntByReference](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/IntByReference.java)
3. [Matrix](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/Matrix.java)

## Menu 
```java
package com.example.sping_portfolio.controllers;

import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;
import java.util.concurrent.RunnableFuture;

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

        Map<Integer, main2> main2 = new HashMap<>();

        main2.put(1, new main2("Matrix", () -> Matrix.main(null)));
        main2.put(2, new main2("IntByReference", () -> IntByReference.main(null)));

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