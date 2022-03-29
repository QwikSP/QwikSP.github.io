---
layout: post
title: Notes for Tech Talks
subtitle: my notes and plans for notes
---
plans for notes...
Take notes on key words and record their definitions. Record any useful tips as well

Notes for TT will go under here...

## 3/21 notes

1. string become token
2. token goes to rpm
3. first 2 numbers go into stack
4. pop numbers
5. operator evaluates
6. next two numbers go into stack
7. pop numbers
8. operator evaluates


### rpnToResult method
This java method processes the revers polish notation and calculates the numbers with precedence.
```java
        private void rpnToResult()
        {
            // Stack used to hold calculation while process RPN
            Stack calculation = new Stack();
//            System.out.println(reverse_polish);
            Double z = 0.0;
            for (String token : reverse_polish)
            {
                //check if token is not operator
//                System.out.println((token));
                if (!isOperator(token)) {
//                    System.out.println((token));
                    calculation.push(token);

                }
                else{
//                    System.out.println(calculation.pop().toString());
                    Double y = Double.parseDouble(calculation.pop().toString());
                    Double x = Double.parseDouble(calculation.pop().toString());

                    if (token.equals("*")){
                        z = x * y;
                    }
                    else if (token.equals("/")){
                        z = x / y;
                    }
                    else if (token.equals("+")){
                        z = x + y;
                    }
                    else if (token.equals("-")){
                        z = x - y;
                    }
                    else if (token.equals("%")){
                        z = x % y;
                    }
//                    System.out.println(z);
                    // Based off of Token operator calculate result

                    // Push result back onto the stack
                    calculation.push(z);
                }
            }
            // Pop final result and set as final result for expression

            result = Double.parseDouble(calculation.pop().toString());
        }

    public static void main(String[] args)
    {
        Calculator simpleMath = new Calculator("100 + 200  * 3");
        System.out.println("Simple Math\n" + simpleMath);

        Calculator parenthesisMath = new Calculator("(100 + 200)  * 3");
        System.out.println("Parenthesis Math\n" + parenthesisMath);

        Calculator allMath = new Calculator("200 % 300 + 5 + 300 / 200 + 1 * 100");
        System.out.println("All Math\n" + allMath);

        Calculator allMath2 = new Calculator("200 % (300 + 5 + 300) / 200 + 1 * 100");
        System.out.println("All Math2\n" + allMath2);

//        Calculator allMath3 = new Calculator("200 % sqrt(300 + 5 + 300) / 200 + 1 * 100");
//        System.out.println("All Math2\n" + allMath2);
    }
}
```



[3/15 Linked Lists Notes](https://github.com/nighthawkcoders/nighthawk_csa/wiki/Tri-3:-Tech-Talk-1:-Linked-Lists-Part-2)

> **_Linked Lists:_**  linked lists are lists that are linked in one direction though variables within each object within the list.
```java
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
```
> **head** is the first node of the linked list
 ```java
     public LinkedList<T> getHead() {
        return this.head;
    }
```
> **tail** is the last node of the linked list
```java
  public LinkedList<T> getTail() {
        return this.tail;
    }
```
>the head of the linked list will link to the next node and so on. The last node (tail) will link to null since there isn't anything else after it.
> **_Doubly Linked Lists:_** these are liked linked lists but the nodes are also linked backwards, towards their previous node.
>A normal linked list will only link to the next node, however a doubly linked lists's node will link to both it's next node and it's previous node.
```java
 public LinkedList(T data, LinkedList<T> node)
    {
        this.setData(data);
        this.setPrevNode(node);
        this.setNextNode(null);
    }
```
> **_The Java Generic T_** is a generic type of perameter for the class it is added to. It will generally appear at the end of the class name with < >. 
```java
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
```



Linked lists are datastructures

They have lists


que john object --> datatype john

head pointer: beginning of list (always slimy in this case)
tail pointer: end of list (southward after southward is added)

deque --> remove head pointer

kinda logical first come first serve
or...
First in First out (FIFO)


Stack- will use push and pop

deque and push to reverse order of stack

a que has a linked list --> que will have date (ie. object john, object calvin, etc)

previous node is node previous

next node is null untill it is added


link list needs to be resized periodically and it needs

arraylist is a cobination of a queue and an array list

Personal Linked List Notes

[Linked List Notes](https://www.youtube.com/watch?v=njTh_OwMljA)

Insertian and deletion is very efficient compared to an array

Doubly linked lists each element is linked to its next and previous element



need to make methods to append rather than just append 
