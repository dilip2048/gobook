## Reversal algorithm for array rotation

This program will rotate the array of size n by d elements.


***Example***:

```json
Input :  arr[] = [1, 2, 3, 4, 5, 6, 7]
         d = 2
Output : arr[] = [3, 4, 5, 6, 7, 1, 2] 
```


&nbsp;


Below is the implementation of the problem:

```go
 
package main
 
import "fmt"
 
// Function to left rotate arr of size n by d
func leftRotate(arr []int, d int) {
    if d == 0 {
        return
    }
    n := len(arr)
    reverseArray(arr, 0, d-1)
    reverseArray(arr, d, n-1)
    reverseArray(arr, 0, n-1)
 
}
 
// Function to reverse arr from index start to end
func reverseArray(arr []int, start int, end int) {
    for start < end {
        temp := arr[end]
        arr[end] = arr[start]
        arr[start] = temp
        start++
        end--
    }
}
 
// Function to print an array
func printArray(arr []int)  {
    n := len(arr)
    for i := 0; i < n; i++ {
        fmt.Printf("%x ", arr[i])
    }
}
 
//Driver program to test above functions
func main() {
    arr := []int{1, 2, 3, 4, 5, 6, 7}
    n := len(arr)
    d := 2
 
    // in case the rotating factor is
    // greater than array length
    d = d % n
    leftRotate(arr, d) // Rotate array by d
    printArray(arr)
}
```