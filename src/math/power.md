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
func power(x int64, y int64) int64 {
	if y == 0 {
		return 1
	}
	if y%2 == 0 {
		return power(x, y/2) * power(x, y/2)
	} else {
		return x * power(x, y/2) * power(x, y/2)
	}
}

/* Program to test function power */
func main() {
	result := power(2, 5)
	println(result)
}
```