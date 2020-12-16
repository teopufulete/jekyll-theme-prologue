---
title: Sorting Algorithms
author: Teo
layout: post
---

<h3> Insertion Sort </h3>
{% highlight java linenos %} public class InsertionSort {
    public static void sort(int array[]) {
        for (int j = 1; j < array.length; j++) {
            int key = array[j];
            int i = j - 1;
            while ((i > -1) && (array[i] < key)) {
                array[i + 1] = array[i];
                i--;
            }
            array[i + 1] = key;
        }
    }

    public static void main(String args[]) {
        int[] arr1 = {31, 41, 59, 26, 41, 58};
        System.out.println("Input array:");
        for(int i:arr1){
            System.out.print(i+" ");
        }
        System.out.println();

        sort(arr1);

        System.out.println("Sorted Array");
        for(int i:arr1){
            System.out.print(i+" ");
        }
    }
}
    {% endhighlight %}

<hr/>

<h3> Merge Sort </h3>
{% highlight java linenos %} public class MergeSort {
    public void merge(int arr[], int low, int mid, int high) {
        int leftLength = mid - low + 1;
        int rightLength = high - mid;

        int LeftArr[] = new int [leftLength + 1];
        int RightArr[] = new int [rightLength + 1];

        LeftArr[leftLength] = Integer.MAX_VALUE;
        RightArr[rightLength] = Integer.MAX_VALUE;

        for (int i = 0; i < leftLength; i++) {
            LeftArr[i] = arr[low + i];
        }

        for (int j = 0; j < rightLength; j++) {
            RightArr[j] = arr[mid + j + 1];
        }

        int i = 0, j = 0;

        for (int k = low; k <= high; k++) {
            if (LeftArr[i] <= RightArr[j]) {
                arr[k] = LeftArr[i];
                i++;
            }
            else {
                arr[k] = RightArr[j];
                j++;
            }
        }
    }

    public void mergeSort(int arr[], int low, int high) {
        if (low < high) {
            int mid = low + (high - low) / 2;
            mergeSort(arr, low, mid);
            mergeSort(arr, mid + 1, high);
            merge(arr, low, mid, high);
        }
    }

    public static void main(String args[]) {
        int input[] = {5, 2, 4, 7, 1, 3, 2, 6};

        MergeSort algo =  new MergeSort();
        algo.mergeSort(input, 0, input.length-1);

        System.out.println("\nSorted array");
        for (int i = 0; i < input.length; i++) {
            System.out.println(input[i]+"");
        }
    }
}
{% endhighlight %}

<hr/>

<h3> Quick Sort </h3> 
{% highlight java linenos %} public class QuickSort {
    private int partition(int arr[], int begin, int end) {
        int pivot = arr[end];
        int i = (begin-1);

        for (int j = begin; j < end; j++) {
            if (arr[j] <= pivot) {
                i++;

                int swapTemp = arr[i];
                arr[i] = arr[j];
                arr[j] = swapTemp;
            }
        }

        int swapTemp = arr[i+1];
        arr[i+1] = arr[end];
        arr[end] = swapTemp;

        return i+1;
    }

    public void sort(int arr[], int begin, int end) {
        if (begin < end) {
            int partitionIndex = partition(arr, begin, end);
            sort(arr, begin, partitionIndex-1);
            sort(arr, partitionIndex+1, end);
        }
    }

    // utility function
    static void printArray(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }

    // Driver program
    public static void main(String args[]) {
        int arr[] = {10, 7, 8, 9, 1, 5};
        int n = arr.length;

        QuickSort ob = new QuickSort();
        ob.sort(arr, 0, n-1);

        System.out.println("sorted array");
        printArray(arr);
    }
}
{% endhighlight %}
<hr/>

<h3> Heap Sort </h3>
{% highlight java linenos %} import java.util.*;

class HeapSort {

    public void sort(int heap[]) {
        int size = heap.length;

        // construct max heap
        for (int i = size / 2 - 1; i >= 0; i--) {
            heapify(heap, size, i);
        }

        // Heap sort
        for (int i = size - 1; i >= 0; i--) {
            int temp = heap[0];
            heap[0] = heap[i];
            heap[i] = temp;
            // Heapify root element
            heapify(heap, i, 0);
        }
    }


    void heapify(int heap[], int n, int i) {
        // find largest value
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && heap[left] > heap[largest])
            largest = left;
        if (right < n && heap[right] > heap[largest])
            largest = right;
        
        // recursively heapify and swap if root is not the largest
        if (largest != i) {
            int swap = heap[i];
            heap[i] = heap[largest];
            heap[largest] = swap;
            heapify(heap, n, largest);
        }
    }


    public static void main(String args[]) {
        //define input array and print it
        int heap[] = {6,2,9,4,10,15,1,13};
        System.out.println("Input Array:" + Arrays.toString(heap));
        //call HeapSort method for given array
        HeapSort hs = new HeapSort();
        hs.sort(heap);
        //print the sorted array
        System.out.println("Sorted Array:" + Arrays.toString(heap));
    }
}
{% endhighlight %}
<hr/>
