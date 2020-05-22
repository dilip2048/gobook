## Adding one to number represented as array of digits

Given a non-negative number represented as an array of digits, add 1 to the number (increment the number represented by the digits). The digits are stored such that the most significant digit is first element of array.


Examples :

```json
Input : [1, 2, 4]
Output : [1, 2, 5]

Input : [9, 9, 9]
Output : [1, 0, 0, 0]
```

Below is the implementation to add 1 to number represented by digits.

```go
package main

import "fmt"

// function to add 1 to the number
func addOne(s []int) []int{
    n := len(s)

    //add 1 to last digit and store the carry
    s[n-1] = s[n-1] + 1
    carry := s[n-1] / 10
    s[n-1] = s[n-1] % 10

    //loop from second last element
    for i := n - 2; i >= 0; i-- {
        if carry == 1 {
            s[i] = s[i] + 1
            carry = s[i] / 10
            s[i] = s[i] % 10
        }
    }

    if carry == 1 {
        s1 := []int{1}
        s1 = append(s1, s...)
        return  s1
    }
    return s
}

func main() {
    slice := []int{0, 7, 9, 9}
    s := addOne(slice)
    print(fmt.Sprintf("%v", s))
}

```

