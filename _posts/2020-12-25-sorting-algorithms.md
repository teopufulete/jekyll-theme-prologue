---
title: Sorting ALgorithms
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

<h3> Heap Sort </h3>
{% highlight java linenos %} 
{% endhighlight %}
<hr/>
