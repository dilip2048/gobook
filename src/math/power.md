## Write a program to calculate pow(x, n)


Examples :

```css
Input : x = 2, n = 3
Output : 8

Input : x = 7, n = 2
Output : 49
```


```go
package main

/* Function to calculate x raised to the power y */
func power(x int64, n int64) int64 {
	if n == 0 {
		return 1
	}
	if n%2 == 0 {
		return power(x, n/2) * power(x, n/2)
	} else {
		return x * power(x, n/2) * power(x, n/2)
	}
}

/* Program to test function power */
func main() {
	result := power(2, 5)
	println(result)
}
```

Time Complexity: O(n)
Space Complexity: O(1)


The above code can be optimized to O(log n) by calculating power(x, y/2) once once. Please find the full code below:

```go
package main

// Function to calculate x raised to the power n
func power(x int64, n int64) int64 {
	if n == 0 {
		return 1
	}
	temp := power(x, n/2)
	if n%2 == 0 {
		return temp * temp
	} else {
		return x * temp * temp
	}

}

func main() {
	result := power(2, 5)
	print(result)
}

```

Time Complexity: O(log n)
Space Complexity: O(1)