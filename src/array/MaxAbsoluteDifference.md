# Maximum absolute difference of value and index sums

You are given an array of N integers, A1, A2 ,…, AN. Return maximum value of `f(i, j)` for all `1 ≤ i, j ≤ N.`
`f(i, j)` is defined as `|A[i] - A[j]| + |i - j|`, where |x| denotes absolute value of x.


For example,

```json
A=[1, 3, -1]

f(1, 1) = f(2, 2) = f(3, 3) = 0
f(1, 2) = f(2, 1) = |1 - 3| + |1 - 2| = 3
f(1, 3) = f(3, 1) = |1 - (-1)| + |1 - 3| = 4
f(2, 3) = f(3, 2) = |3 - (-1)| + |2 - 3| = 5

So, we return 5.
```

Below is the brute force approch of the given problem.

```go
package main

import "math"

// This method with return maximum absolute difference
func getMaxAbsoluteDifference(A []int) int{
	max := 0
	for i := 0; i < len(A)-1; i++ {
		for j := i + 1; j < len(A); j++ {
			sum := math.Abs(float64(A[i]-A[j])) + math.Abs(float64(i-j))
			if int(sum) > max {
				max = int(sum)
			}
		}
	}
	return max
}

func main() {
	array := []int{ -70, -64, -6, -56, 64,
		61, -57, 16, 48, -98 }
	max := getMaxAbsoluteDifference(array)
	println(max)
}
```

Output: 167

Time Complexity: O(n^2)


The time complexity O(n) can be acheived using the properties of absolute values. For more explaination, please refer https://www.geeksforgeeks.org/maximum-absolute-difference-value-index-sums/.

Please find below the go implementation.

```go
package main

import (
	"fmt"
	"math"
)

// This method with return maximum absolute difference
func getMaxAbsoluteDifference(A []int) int {
	max1 := math.MinInt64
	min1 := math.MaxInt64
	max2 := math.MinInt64
	min2 := math.MaxInt64
	for i := 0; i < len(A); i++ {
		max1 = int(math.Max(float64(max1), float64(A[i]+i)))
		min1 = int(math.Min(float64(min1), float64(A[i]+i)))
		max2 = int(math.Max(float64(max2), float64(A[i]-i)))
		min2 = int(math.Min(float64(min2), float64(A[i]-i)))
	}
	return int(math.Max(float64(max1-min1), float64(max2-min2)))
}

func main() {
	array := []int{-70, -64, -6, -56, 64,
		61, -57, 16, 48, -98}
	max := getMaxAbsoluteDifference(array)
	m := fmt.Sprintf("%v", max)
	println(m)
}
```

Output: 167

Time Complexity: O(n)