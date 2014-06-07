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

