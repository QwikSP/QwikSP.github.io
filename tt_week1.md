---
layout: page
title: Week 1 notes
subtitle: Week 1
---

[3/15 Linked Lists Notes](https://github.com/nighthawkcoders/nighthawk_csa/wiki/Tri-3:-Tech-Talk-1:-Linked-Lists-Part-2)
[Run Time](https://replit.com/github/QwikSP/DataStructures)


## Queue code
Queues and dequeues words
```java
**public void add(T data) {
        // add new object to end of Queue
        LinkedList<T> tail = new LinkedList<>(data, null);

        if (head == null)  // initial condition
            this.head = this.tail = tail;
        else {  // nodes in queue
            this.tail.setNextNode(tail); // current tail points to new tail
            this.tail = tail;  // update tail
        }

    }
    //remove tail
    public void remove(T data) {
        LinkedList<T> tail = new LinkedList<>(data, null);
        if(head == null){
            throw new RuntimeException("Deque is empty");
        }

        if(head.getNext() == null){
            tail = null;
        }else{
            // previous of next node (new first) becomes null
            head.getNext().setPrevNode(tail);
        }
        head = head.getNext();
    }**
```

## Sort Queue
Sort the queue when numbers are inputted
```java
 public void sort(QueueManager seriesOfObjects) {

    // intialize variables
        T previous = null;
        T current = null;
        //sort
        ArrayList<Integer> emptyAL = new ArrayList<Integer>();
        for (T data : queue) {
            emptyAL.add(Integer.valueOf((String) data));
        }
        for (Object data : seriesOfObjects.queue) {
            emptyAL.add(Integer.valueOf((String) data));
        }
        int n = emptyAL.size();
        for (int i = 1; i < n; ++i) {
            int key = emptyAL.get(i);
            int j = i - 1;

            /* Move elements of arr[0..i-1], that are
               greater than key, to one position ahead
               of their current position */
            while (j >= 0 && emptyAL.get(j) > key) {
                emptyAL.set(j + 1, emptyAL.get(j));
                j = j - 1;
            }
            emptyAL.set(j + 1, key);
        }
        System.out.println();
        for (int data : emptyAL) {
            System.out.print(data + " -> ");
        }
        System.out.print("nil");


    }
```

## Stack
Stack will reverse the order of the numbers
```java
 static Stack<Integer> st= new Stack<>();
    private int numbers;

    //push all the numbers into the stack
    public static void push_digits(int number)
    {
        while(number != 0)
        {
            st.push(number % 10);
            number = number / 10;
        }
    }

    //reverse the order of the numbesr
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
```

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
