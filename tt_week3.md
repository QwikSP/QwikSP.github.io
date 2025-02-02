---
layout: page
title: Week 3 notes
subtitle: Week 3
---

[Run Time](https://replit.com/github/QwikSP/DataStructures)
## 3/28 notes

### Best Sort is Merge Sort
Most Efficiant with O(log(n))

### Example output
Selection Sort

## Analysis on the Sorts

| Sort Type | Average runtime with highs and lows | Average runtime with highs and lows omitted | Big O complexity |
| :---   | :---    | :---    | :---    |
| Bubble | 0.002327683 | 0.00219408 | O(n²) in worst case; O(n) in the best case | 
| Insertion | 0.031171416 | 0.03052125 | O(N^2) in worst case;  O(N) in the best case |
| Selection | 0.033331483 | 0.0323154 | O(n²) regardless|
| Merge (Best) | 0.00590485 | 0.00578954 | O(n log n) regardless (most efficient) |

# of swaps: 4999     # of comparisons: 12497500
High: 5000   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 5000   Low: 1
# of swaps: 4999     # of comparisons: 12497500
High: 4997   Low: 1
# of swaps: 4999     # of comparisons: 12497500
High: 4995   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 4998   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 4999   Low: 1
# of swaps: 4999     # of comparisons: 12497500
High: 4998   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 5000   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 4997   Low: 1
# of swaps: 4999     # of comparisons: 12497500
High: 4998   Low: 2
# of swaps: 4999     # of comparisons: 12497500
High: 4999   Low: 0
# of swaps: 4999     # of comparisons: 12497500
High: 4997   Low: 0
Average random: 2493
Total Nanoseconds: 546916700
Total Seconds: 0.5469167

### Bubble Sort
Bubble Sort will swap the previous number with the curent number if the previous number is greater than the current number.
- o(n)
```java
  public ArrayList<Integer> sort(ArrayList original) {
        ArrayList<Integer> temp = new ArrayList<>();
        temp = original;
        int n = temp.size();
        //swap the numbers loop
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
Merge sort splits an aray in half until the the numbers are alone then it reconstructs the arrays but with the numbers being inputted into the new array in least to greatest order
- O(nLogn)
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
Selection sort swaps the lowest number with the current number over and over until the Array List is sorted
- Big O notation: O(n2)
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
Insertion sort starts from the left and moves the current number to the left until the number to the right of it is greater than the current number.
- O(n2)
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
        //intialize variables
        arr = original;
        int n = arr.size();
        //for loop until the arary is sorted
        for (int i = 1; i < n; ++i) {
            int key = arr.get(i);
            int j = i - 1;
            while (j >= 0 && arr.get(j) > key) {
                //swaping numbers
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