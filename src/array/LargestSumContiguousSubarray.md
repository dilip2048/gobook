## Largest Sum Contiguous Subarray

The maximum sum contiguous subarray for an array { -2, -3, 4, -1, -2, 1, 5, -3 } is 7 with subarray {4, -1, -2, 1, 5}. 

Please find the go program below:

```go
package main

// method to print largest contiguous array sum
func findMaxSum(a []int) int {
	currMax := a[0]
	maxSofar := a[0]
	for i := 1; i < len(a); i++ {
		if a[i] + currMax > a[i]{
			currMax = a[i] + currMax
		}else {
			currMax = a[i]
		}
		if currMax > maxSofar{
			maxSofar = currMax
		}
	}
	return maxSofar
}

func main() {
	array := []int{-2, -3, 4, -1, -2, 1, 5, -3}
	println(findMaxSum(array))
}
```
Output: 7

The space and time complexity is O(n).

To print the subarray, we need to track the start and end of the subarray with maximum sum. Plese find the program below:

```go
package main

import (
	"fmt"
	"math"
)

// method to print largest contiguous array sum
func findMaxSubarray(a []int) (int, int) {
	start := 0
	s := 0
	end := 0
	currentMax := 0
	maxSoFar := math.MinInt64
	for i := 0; i < len(a); i++ {
		currentMax = a[i] + currentMax
		if currentMax > maxSoFar {
			maxSoFar = currentMax
			start = s
			end = i
		}
		if currentMax < 0 {
			currentMax = 0
			s = i + 1
		}
	}
	return start, end
}

func main() {
	array := []int{-2, -3, 4, -1, -2, 1, 5, -3}
	start, end := findMaxSubarray(array)
	fmt.Println(array[start : end+1])
}
```

Output: [4 -1 -2 1 5]

The space and time complexity is O(n).