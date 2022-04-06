---
layout: post
title: Week 1 Challenge 1,2,3
subtitle: work for linked lists part 2
---
[Run Time](https://replit.com/github/QwikSP/DataStructures)

## GitHub Links
1. [Sort Folder](https://github.com/QwikSP/CSA-Tri-3/tree/master/src/main/java/com/example/sping_portfolio/controllers/Sort)

## Analysis on the Sorts
| Sort Type | Average runtime with highs and lows | Average runtime with highs and lows omitted | Big O complexity |
| :---   | :---    | :---    | :---    |
| Bubble | 0.002327683 | 0.00219408 | O(n²) in worst case; O(n) in the best case | 
| Insertion | 0.031171416 | 0.03052125 | O(N^2) in worst case;  O(N) in the best case |
| Selection | 0.033331483 | 0.0323154 | O(n²) regardless|
| Merge (Best) | 0.00590485 | 0.00578954 | O(n log n) regardless (most efficient) |

![animation](https://miro.medium.com/max/1400/1*bPpvELo9_QqQsDz7CSbwXQ.gif)
## Sort Code
```java
public class Sorts {
    private ArrayList<Integer> data = new ArrayList<>();
    private final Duration timeElapsed;

    public Sorts(int size) {
        Instant start = Instant.now();  // time capture -- start
        // build an array
        for (int i = 0; i < size; i++) {
            data.add((int)(Math.random() * (size+1)));
        }
        // use Inheritance and Polymorphism to replace data.sort with your own algorithm
        data = sort(data);
        Instant end = Instant.now();    // time capture -- end
        this.timeElapsed = Duration.between(start, end);
    }

    public ArrayList sort(ArrayList origianl) {
        return origianl;
    }

    public ArrayList<Integer> getData() {
        return data;
    }

    public int getTimeElapsed() {
        return timeElapsed.getNano();
    }


    public static void main(String[] args) {
        int sum=0, time=0, TIMES=12, SIZE=5000;

        //Bubble Sort

        System.out.println("\n\n" + "Bubble Sort" + "\n\n");
        for(int i=0; i< TIMES; i++) {
            BubbleSort s = new BubbleSort(SIZE);
            for(int j = 0; j<s.getData().size(); j++) {
                sum += s.getData().get(j);
            }
            time += s.getTimeElapsed();
        }
        System.out.println("Average random: " + sum / (TIMES*SIZE));
        System.out.println("Total Nanoseconds: " + time );
        System.out.println("Total Seconds: " + time /1000000000.0);

        //Selection Sort
        System.out.println("\n\n" + "Selection Sort" + "\n\n");
        sum = 0; time=0;

        for(int i=0; i< TIMES; i++) {
            SelectionSort s = new SelectionSort(SIZE);
            for(int j = 0; j<s.getData().size(); j++) {
                sum += s.getData().get(j);
            }
            time += s.getTimeElapsed();
        }
        System.out.println("Average random: " + sum / (TIMES*SIZE));
        System.out.println("Total Nanoseconds: " + time );
        System.out.println("Total Seconds: " + time /1000000000.0);

        //Insertion Sort
        System.out.println("\n\n" + "Insertion Sort" + "\n\n");
        sum = 0; time=0;

        for(int i=0; i< TIMES; i++) {
            InsertionSort s = new InsertionSort(SIZE);
            for(int j = 0; j<s.getData().size(); j++) {
                sum += s.getData().get(j);
            }
            time += s.getTimeElapsed();
        }
        System.out.println("Average random: " + sum / (TIMES*SIZE));
        System.out.println("Total Nanoseconds: " + time );
        System.out.println("Total Seconds: " + time /1000000000.0);

        //Merge Sort
        System.out.println("\n\n" + "Merge Sort" + "\n\n");
        sum = 0; time=0;

        for(int i=0; i< TIMES; i++) {
            MergeSort s = new MergeSort(SIZE);
            for(int j = 0; j<s.getData().size(); j++) {
                sum += s.getData().get(j);
            }
            time += s.getTimeElapsed();
        }
        System.out.println("Average random: " + sum / (TIMES*SIZE));
        System.out.println("Total Nanoseconds: " + time );
        System.out.println("Total Seconds: " + time /1000000000.0);
    }


}
```
### Bubble Sort

```java
  public ArrayList<Integer> sort(ArrayList original) {
        ArrayList<Integer> temp = new ArrayList<>();
        temp = original;
        int n = temp.size();
        for (int i = 0; i < n-1; i++)
            for (int j = 0; j < n-i-1; j++)
                if (temp.get(j) > temp.get(j+1))
                {
                    comparison++;
                    swap++;
                    // swap arr[j+1] and arr[j]
                    int tempNub = temp.get(j);
                    temp.set(j, temp.get(j+1));
                    temp.set(j+1, tempNub);
                }
//        System.out.print("(");
//        for (Integer p : temp) {
//            System.out.print(p + " ,");
//        }
//        System.out.print(")");
        System.out.println("# of swaps: " + swap + "     # of comparisons: " + comparison);
        return temp;
    }
```

### Merge Sort

```java
 public void merge(ArrayList arr, int l, int m, int r)
    {
        // Find sizes of two subarrays to be merged


        int n1 = m - l + 1;
        int n2 = r - m;

        /* Create temp arrays */
        int L[] = new int[n1];
        int R[] = new int[n2];

        /*Copy data to temp arrays*/
        for (int i = 0; i < n1; ++i)
            L[i] = (int) arr.get(l + i);
        for (int j = 0; j < n2; ++j)
            R[j] = (int) arr.get(m + 1 + j);

        /* Merge the temp arrays */

        // Initial indexes of first and second subarrays
        int i = 0, j = 0;

        // Initial index of merged subarray array
        int k = l;
        while (i < n1 && j < n2) {
            comparison++;
            if (L[i] <= R[j]) {
                arr.set(k, L[i]);
                i++;
            }
            else {
                arr.set(k, R[j]);
                j++;
            }
            k++;
        }

        /* Copy remaining elements of L[] if any */
        while (i < n1) {
            arr.set(k, L[i]);
            i++;
            k++;
        }

        /* Copy remaining elements of R[] if any */
        while (j < n2) {
            arr.set(k, R[j]);
            j++;
            k++;
        }
    }

    // Main function that sorts arr[l..r] using
    // merge()
    public ArrayList sort(ArrayList arr) {
        int l = 0;
        int r = arr.size()-1;
        if (l < r) {
            comparison++;
            // Find the middle point
            int m = l + (r - l) / 2;

            // Sort first and second halves
            sortS(arr, l, m);
            sortS(arr, m + 1, r);

            // Merge the sorted halves
            merge(arr, l, m, r);
        }
        System.out.println("# of comparisons: " + comparison);
        return arr;
    }

    public void sortS(ArrayList arr, int l, int r) {
        if (l < r) {
            comparison++;
            // Find the middle point
            int m = l + (r - l) / 2;

            // Sort first and second halves
            sortS(arr, l, m);
            sortS(arr, m + 1, r);

            // Merge the sorted halves
            merge(arr, l, m, r);
        }

    }
```


### Selection Sort

```java
 public ArrayList<Integer> sort(ArrayList original) {
        ArrayList<Integer> arr;
        arr = original;
        int n = arr.size();
        for (int i = 0; i < n-1; i++)
        {
            // Find the minimum element in unsorted array
            int min_idx = i;
            for (int j = i+1; j < n; j++) {
                if (arr.get(j) < arr.get(min_idx)) {
                    min_idx = j;
                }
                comparison++;
            }

            // Swap the found minimum element with the first
            // element
            swap++;
            int temp = arr.get(min_idx);
            arr.set(min_idx, arr.get(i));
            arr.set(i, temp);
        }
        System.out.println("# of swaps: " + swap + "     # of comparisons: " + comparison);
        return arr;
    }
```


### Insertion sort

```java
public class InsertionSort extends Sorts {

    ArrayList sorted;
    int swap = 0;
    int comparison = 0;
    public InsertionSort(int size) {
        super(size);

    }


    public ArrayList<Integer> sort(ArrayList original) {
        ArrayList<Integer> arr = new ArrayList<>();
        arr = original;
        int n = arr.size();
        for (int i = 1; i < n; ++i) {
            int key = arr.get(i);
            int j = i - 1;
            while (j >= 0 && arr.get(j) > key) {
                swap++;
                comparison = comparison + 2;
                arr.set(j + 1, arr.get(j));
                j = j - 1;
            }
            arr.set(j + 1,key);
            swap++;
        }

        System.out.println("# of swaps: " + swap + "     # of comparisons: " + comparison);
        return arr;
    }
}
```
