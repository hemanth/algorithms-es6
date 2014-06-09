As of now in the latest browser or node, typing `class` would yield:

```js
> class
SyntaxError: Unexpected reserved word
```
This repo is a WIP that should slowly grow into a collection of implementation of various algorithms with JS using ES6 constructs!


Let's start with Sorting Algorithms!

Before we create classes of each of the sorting algorithms, let's create a base class named `Sorter`

```js
class Sorter {
  constructor(nums) {
    this.nums = nums;
  }
}
```

#Bubble Sort

PesudoCode:

```
repeat
    hasChanged := false
	decrement itemCount
    repeat with index from 1 to itemCount
		if (item at index) > (item at (index + 1))
				swap (item at index) with (item at (index + 1))
                hasChanged := true
until hasChanged = false
```

![](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

Worst case complexity is `O(n^2)`

```js
class BubbleSort extends Sorter {

  constructor(nums) {
    super(nums);
  }
  
  sort() {
    var length = this.nums.length;
     do {
        var swapped = false;
        for(var i = 0; i < length; ++i) {
          if (this.nums[i] > this.nums[i+1]) {
            [this.nums[i],this.nums[i+1]] = [this.nums[i+1], this.nums[i]];
            swapped = true;
          }
        }
    } while(swapped == true);
	return this.nums;
  }
}
```

```
var bubble = new BubbleSort([-1,0,-11,42,32,3]);

console.log(bubble.sort()); // [-11,-1,0,3,32,42]
```

#Insertion Sort

PesudoCode:

```
function insertionSort(array A)
    for i from 1 to length[A]-1 do
        value := A[i] 
        j := i-1
        while j >= 0 and A[j] > value do
            A[j+1] := A[j]
            j := j-1
        done
        A[j+1] = value
    done
```

![](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)


```javascript
class InsertionSort extends Sorter {
  constructor(nums){
    super(nums)
  }
  
  sort() {
    for(var i = 1; i < this.nums.length; i++){
      var value = this.nums[i];
      var j = i - 1;
      while(j >= 0 && this.nums[j] > value){
        this.nums[j + 1] = this.nums[j];
        j = j - 1;
      }
      this.nums[j + 1] = value;
    }
    return this.nums;
  }
}
```

```
var insertion = new InsertionSort([3,4,1,2,0]);

console.log(insertion.sort()); // 0,1,2,3,4
```

#Selection Sort

PesudoCode:

```
for i = 0 to numItems - 1
    for  j = i+1 to numItems               
        if A[i] > A[j]
            A[i] <-> A[j]         
        End If    
    Next j
Next i
```

![](http://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

```js
class SelectionSort extends Sorter {
  constructor(nums){
    super(nums);
  }
  sort(){
    var len = this.nums.length,
        min,i,j;

    for (i=0; i < len; i++){
        min = i;
        for (j=i+1; j < len; j++){
            if (this.nums[j] < this.nums[min]){
                min = j;
            }
        }
        if (i != min){
            [this.nums[i],this.nums[min]] = [this.nums[min],this.nums[i]];
        }
    }
    return this.nums;
  }
}
```

```js
var selection = SelectionSort([1,2,-1,0,4,5]);
console.log(selection.sort()); // -1,0,1,2,4,5
```