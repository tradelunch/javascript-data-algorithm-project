# Heap

> Time: \
> buildHeap: O(NLogN) \
> insert, remove: O(LogN) → O(H)

> Space: O(N)

```javascript

class Heap {
    constructor(arr, predicate = (a, b) => a <= b) {
        this.predicate = predicate;
        this.size = arr.length;
        this.heap = this.buildHeap(arr);
    }

    buildHeap(arr) {
        let currentIndex = Math.floor((arr.length - 1 - 1) / 2);
        while (currentIndex >= 0) {
            this.siftDown(arr, currentIndex, arr.length - 1);
            currentIndex--;
        }

        return arr;
    }

    insert(v) {
        this.heap.push(v);
        this.size++;

        this.siftUp(this.heap, this.heap.length - 1);

    }

    remove(v) {
        this.swap(this.heap, 0, this.heap.length - 1);
        const elementToRemove = this.heap.pop();
        this.size--;
        
        this.siftDown(this.heap, 0, this.heap.length - 1);
        return elementToRemove;
    }

    siftUp(heap, currentIndex) {
        let parentIndex = Math.floor((currentIndex - 1) / 2);
        while (parentIndex >= 0) {
            if (this.predicate(heap[parentIndex], heap[currentIndex])) {
                break;
            }

            this.swap(heap, parentIndex, currentIndex);
            currentIndex = parentIndex;
            parentIndex = Math.floor((currentIndex - 1) / 2);
        }
        return heap;
    }

    siftDown(heap, currentIndex, endIndex) {
        let left = currentIndex * 2 + 1;

        while (left <= endIndex) {
            let min = left;
            const right = currentIndex * 2 + 2;
            if (heap[right] !== undefined && this.predicate(heap[right], heap[min])) {
                min = right;
            }

            if (this.predicate(heap[currentIndex], heap[min])) break;
            this.swap(heap, currentIndex, min);
            currentIndex = min;
            left = currentIndex * 2 + 1;
        }

        return heap;
    }

    swap(arr, a, b) {
        [arr[b], arr[a]] = [arr[a], arr[b]];
    }

    clear() {
        this.heap = [];
        this.size = [];
    }

}

```



