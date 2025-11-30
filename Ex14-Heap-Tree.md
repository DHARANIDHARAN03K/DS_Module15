# Ex3(D) Heap Tree
## DATE:06-09-2025
## AIM:
To write a Java function to delete an element in a Heap Tree.

## Algorithm
1.	Start
2.	Find the index of the element num in the array.
3.	Swap the element to be deleted with the last element in the array.
4.	Decrease the heap size by 1.
5.	Start heapifying from the last non-leaf node (index size/2 - 1).
6.	Call heapify() to restore the heap property for each node.
7.	End

## Program:
Java

/*
Program to delete an element in a Heap Tree
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/
public class HeapTree {
    static int size;

    static void swap(int[] array, int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }

    static void heapify(int[] array, int n, int i) {
        int largest = i;
        int left = 2*i + 1;
        int right = 2*i + 2;

        if (left < n && array[left] > array[largest])
            largest = left;
        if (right < n && array[right] > array[largest])
            largest = right;

        if (largest != i) {
            swap(array, i, largest);
            heapify(array, n, largest);
        }
    }

    static void deleteRoot(int[] array, int num) {
        int i;
        for (i = 0; i < size; i++) {
            if (array[i] == num) {
                break;
            }
        }
        swap(array, i, size - 1);
        size -= 1;
        for (i = size/2 - 1; i >= 0; i--) {
            heapify(array, size, i);
        }
    }

    public static void main(String[] args) {
        int[] heap = {50, 30, 40, 10, 5, 20};
        size = heap.length;
        deleteRoot(heap, 30);
        for (int i = 0; i < size; i++) {
            System.out.print(heap[i] + " ");
        }
    }
}

## Output:
50 10 40 5 20 

## Result:
Thus, the Java function to delete an element in a Heap Tree is implemented successfully.
