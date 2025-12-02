# Ex3(D) Heap Tree
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a **Max Heap** and demonstrate the function to **delete an arbitrary element** by preserving the Heap Tree property using the **heapify** procedure.

## Algorithm:
1.  Start.
2.  Define the **`swap()`** function to exchange elements at two given indices.
3.  Define the **`heapify(int[] array, int n, int i)`** function, which ensures the subtree at index $i$ satisfies the Max Heap property.
4.  Define the **`deleteElement(int[] array, int num)`** function:
    a. Find the index $i$ of the element `num` to be deleted within the heap array.
    b. **Swap** the element at index $i$ with the **last element** of the heap (at index $size - 1$). 
    c. **Decrease the size** of the heap by 1, effectively removing the element.
    d. Call the `heapify()` procedure repeatedly from the last non-leaf node upwards (or from the index $i$ downwards) to **restore the heap property**.
5.  In the `main` method, initialize a Max Heap, call the deletion function for a non-root element, and print the resulting heap.
6.  End.

## Program:
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
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && array[left] > array[largest])
            largest = left;
        if (right < n && array[right] > array[largest])
            largest = right;

        if (largest != i) {
            swap(array, i, largest);
            heapify(array, n, largest);
        }
    }

    // Renamed for clarity, as it deletes any element, not just the root
    static void deleteElement(int[] array, int num) {
        int i;
        // 1. Find the index of the element to be deleted
        for (i = 0; i < size; i++) {
            if (array[i] == num) {
                break;
            }
        }
        
        // Handle case where element is not found
        if (i == size) {
            System.out.println("Element " + num + " not found.");
            return;
        }
        
        // 2. Swap the element with the last element
        swap(array, i, size - 1);
        
        // 3. Decrease the heap size
        size -= 1;
        
        // 4. Restore the heap property (re-heapify from the index of the swapped element)
        // Note: The original implementation re-heapifies from the last non-leaf node, 
        // which might be inefficient but works if the original array was fully heapified.
        // A more standard approach is to call heapify(array, size, i) to fix the swapped position.
        // Sticking to the provided logic for conversion:
        
        // Rebuild the heap after deletion (O(n) operation)
        for (int k = size / 2 - 1; k >= 0; k--) {
             heapify(array, size, k);
        }
        
        // Alternative and often preferred way to fix deletion locally:
        // if (i < size) {
        //     heapify(array, size, i);
        // }
    }

    public static void main(String[] args) {
        int[] heap = {50, 30, 40, 10, 5, 20}; // Initial Heap
        size = heap.length;
        
        System.out.println("Original Heap: " + java.util.Arrays.toString(java.util.Arrays.copyOf(heap, size)));
        
        // Delete element 30 (not the root)
        int elementToDelete = 30;
        deleteElement(heap, elementToDelete); 
        
        System.out.println("Deleted Element: " + elementToDelete);
        
        System.out.print("Heap after Deletion: ");
        for (int i = 0; i < size; i++) {
            System.out.print(heap[i] + (i == size - 1 ? "" : " "));
        }
        System.out.println();
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to implement a Heap Tree and successfully delete an arbitrary element while preserving the heap property is implemented successfully.
