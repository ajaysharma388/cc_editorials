Editorial: 💡 Merge K sorted Arrays

Algorithm
Create an result[] of size n*k.
Create Min-Heap of type HeapNode.( HeapNode- Every Node will store the data and the list no from which it belongs).
Now take one element from each of the K list and create HeapNode object and insert into min-Heap.
Extract the minimum Node from the min-Heap, insert the data into result array.
The extracted node will also contain the list to which it belongs, insert the next element from that list into min-Heap.
If any point of time any list gets over, insert +∞ into min-Heap.
Keep repeating until all the K list gets over.

#include <iostream>
#include <limits.h>
using namespace std;
int arr[1000][1000];
class minHeapNode {
    public:
    int element;
    int i; // Index of the array from which the element is taken
    int j; // Index of next element to be picked in the array
};
void swap(minHeapNode *x, minHeapNode *y) {
    minHeapNode temp = *x;
    *x = *y;
    *y = temp;
}
class minHeap {
    minHeapNode *harr; // Pointer to array of elements in heap
    int heap_size; // Size of min Heap

public:
    int left(int i) {return (2*i + 1);}
    int right(int i) {return (2*i + 2);}
    minHeapNode getMin() {return harr[0];}
    void swap(minHeapNode *x, minHeapNode *y) {
        minHeapNode temp = *x;
        *x = *y;
        *y = temp;
    }
    void minHeapify(int i) {
        int l=left(i);
        int r=right(i);
        int smallest = i;
        if(l<heap_size and harr[l].element < harr[i].element)
            smallest=l;
        if(r<heap_size and harr[r].element < harr[smallest].element)
            smallest=r;
        if(smallest != i){
            swap(&harr[i], &harr[smallest]);
            minHeapify(smallest);
        }
    }
    minHeap(minHeapNode a[], int size) {
        heap_size = size;
        harr = a;
        int i = (heap_size-1)/2;
        while(i>=0) {
            minHeapify(i);
            i--;
        }
    }
    void replaceMin(minHeapNode x) {harr[0]=x; minHeapify(0);}
};
int *mergeKArrays(int n,int k) {
    int *output = new int[n*k];
    minHeapNode *harr = new minHeapNode[k];
    for(int i=0;i<k;i++) {
        harr[i].element = arr[i][0];
        harr[i].i = i;
        harr[i].j = 1;
    }
    minHeap hp(harr, k);
    for(int count=0;count<n*k;count++) {
        minHeapNode root = hp.getMin();
        output[count] = root.element;
        if(root.j < n) {
            root.element = arr[root.i][root.j];
            root.j+=1;
        } else {
            root.element = INT_MAX;
        }
        hp.replaceMin(root);
    }

    return output;

}
int main(int argc, char const *argv[])
{
    int x, y;
    cin>>x>>y;
    for(int i=0;i<x;i++) {
        for(int j=0;j<y;j++) {
            cin>>arr[i][j];
        }
    }
    int *output = mergeKArrays(y,x);
    for(int i=0;i<x*y;i++) {
        cout<<output[i]<<" ";
    }
    return 0;
}
Lang - Java

private static class Pair implements Comparable {
        int data;
        int listNo;
        int idxNo;

        @Override
        public int compareTo(Pair o) {
            return o.data - this.data;
        }

    }

    public static void mergeKSortedLists(ArrayList> lists) {

        HeapGeneric heap = new HeapGeneric<>();

        // make a pair and put in heap
        for (int i = 0; i < lists.size(); i++) {
            Pair np = new Pair();
            np.data = lists.get(i).get(0);
            np.idxNo = 0;
            np.listNo = i;

            heap.add(np);
        }

        while (!heap.isEmpty()) {

            Pair rp = heap.remove();

            // print
            System.out.println(rp.data);

            // idx increase
            rp.idxNo++;

            // re-insert only when idx is in range
            if (rp.idxNo < lists.get(rp.listNo).size()) {
                rp.data = lists.get(rp.listNo).get(rp.idxNo);
                heap.add(rp);
            }

        }

    }