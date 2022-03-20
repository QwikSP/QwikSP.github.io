---
layout: post
title: Week 1 Challenge 1,2,3
subtitle: work for linked lists part 2
---
[Run Time](https://replit.com/@Qwiks/CSATri3#Main.java)

## GitHub Links
1. [challenge 1](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/LinkedLists2/LinkedList.java)
2. [challenge 2](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/LinkedLists2/Sort.java)
3. [challenge 3](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/LinkedLists2/stack2.java)
4. [Queue](https://github.com/QwikSP/CSA-Tri-3/blob/master/src/main/java/com/example/sping_portfolio/controllers/LinkedLists2/Queue.java)

## challenge 1
```java
package com.example.sping_portfolio.controllers.LinkedLists2;

/**
 *  Implementation of a Double Linked List;  forward and backward links point to adjacent Nodes.
 *
 */

public class LinkedList<T>
{
    private T data;
    private LinkedList<T> prevNode, nextNode;

    /**
     *  Constructs a new element
     *
     * @param  data, data of object
     * @param  node, previous node
     */
    public LinkedList(T data, LinkedList<T> node)
    {
        this.setData(data);
        this.setPrevNode(node);
        this.setNextNode(null);
    }

    /**
     *  Clone an object,
     *
     * @param  node  object to clone
     */
    public LinkedList(LinkedList<T> node)
    {
        this.setData(node.data);
        this.setPrevNode(node.prevNode);
        this.setNextNode(node.nextNode);
    }

    /**
     *  Setter for T data in DoubleLinkedNode object
     *
     * @param  data, update data of object
     */
    public void setData(T data)
    {
        this.data = data;
    }

    /**
     *  Returns T data for this element
     *
     * @return  data associated with object
     */
    public T getData()
    {
        return this.data;
    }

    /**
     *  Setter for prevNode in DoubleLinkedNode object
     *
     * @param node, prevNode to current Object
     */
    public void setPrevNode(LinkedList<T> node)
    {
        this.prevNode = node;
    }

    /**
     *  Setter for nextNode in DoubleLinkedNode object
     *
     * @param node, nextNode to current Object
     */
    public void setNextNode(LinkedList<T> node)
    {
        this.nextNode = node;
    }


    /**
     *  Returns reference to previous object in list
     *
     * @return  the previous object in the list
     */
    public LinkedList<T> getPrevious()
    {
        return this.prevNode;
    }

    /**
     *  Returns reference to next object in list
     *
     * @return  the next object in the list
     */
    public LinkedList<T> getNext()
    {
        return this.nextNode;
    }

    public LinkedList<T> getObject() {
        return (LinkedList<T>) this.data;
    }

//    public Object getObject() {
//
//        return queue.getHead();
//    }

}

```
## challenge 2
```java
package com.example.sping_portfolio.controllers.LinkedLists2;

public class Sort {

    public static void main(String[] args)
    {
        // Create iterable Queue of Words
        Object[] number1 = new String[] { "1", "4", "5", "8"};
        Object[] number2 = new String[] { "2", "3", "6", "7"};
//        QueueManager qNumb1 = new QueueManager("number1", number1);
//        QueueManager qNumb2 = new QueueManager("number2", number2);
        QueueManager q1 = new QueueManager(number1);
        q1.getQueue();
        QueueManager q2 = new QueueManager(number2);
        q2.getQueue();
        q1.sort(q2);


    }
}
```



## challenge 3
```java
package com.example.sping_portfolio.controllers.LinkedLists2;
import java.util.Stack;
public class stack2 {

    static Stack<Integer> st= new Stack<>();
    private int numbers;

    public static void push_digits(int number)
    {
        while(number != 0)
        {
            st.push(number % 10);
            number = number / 10;
        }
    }

    public static String reverse_number(int number)
    {

        push_digits(number);
        int reverse = 0;
        int i = 1;

        while (!st.isEmpty()) {
            reverse = reverse + (st.peek() * i);

            st.pop();
            i = i * 10;
        }
        String temp = String.valueOf(reverse);
        String newString = "";
        for (int j = 0; temp.length() > j; j++) {
            newString += temp.charAt(j) + " ";
        }


        return newString;
    }

    public static void main(String[] args)
    {
        Object[] SL = new String[] {"1", "2", "3"};
        QueueManager stac = new QueueManager(SL);
        System.out.println("After: " + reverse_number(stac.getNumbers()));

    }
}
// This code is contributed by Sumit Ghosh


```