---
title: 02 - Logic and Loops
description: 
published: true
date: 2020-07-06T17:55:57.378Z
tags: 
editor: markdown
---

# Statements
Your content here

## if / else if / else

``` go
if <boolean expression 1> {
	<code block>
} else if <boolean expression 2> {
	<code block>
} else {
	<code block>
}
```


## switch

"expression switch"
"type switch"

```go
switch <initial statement>; <expresion> {
case <expresion>:
  <statements>
case <expresion>, <expresion>:
  <statements>
default:
  <statements>
}
```

## Loops

## for
```go
// used with slices and arrays
for <initial statement>; <condition>; <post statement> {
  <statements>
}

// used with maps types → range instead of condition
for <key>, <value> := range <map> {
  <statements>
}
```

## code
```go

// · Exercise 2.05: Using a switch Statement

package main

import (
	"fmt"
	"time"
)

func main() {
	dayBorn := time.Monday
	switch dayBorn {
	case time.Monday:
		fmt.Println("on Monday")
	case time.Tuesday:
		fmt.Println("on Tuesday")
	case time.Wednesday:
		fmt.Println("on Wednesday")
	case time.Thursday:
		fmt.Println("on Thursday")
	case time.Friday:
		fmt.Println("on Friday")
	case time.Saturday:
		fmt.Println("on Saturday")
	case time.Sunday:
		fmt.Println("on Sunday")
	default:
		fmt.Println("Error, you not born yet!")
	}
}

// · Exercise 2.06: switch Statements and Multiple case Values

package main

import (
	"fmt"
	"time"
)

func main() {
	bornDay := time.Sunday
	switch bornDay {
	case time.Monday, time.Tuesday, time.Wednesday, time.Thursday, time.Friday:
		fmt.Printf("you born on weekday!")
	case time.Saturday, time.Sunday:
		fmt.Println("you born on weekend")
	}
}

// · Exercise 2.07: Expressionless switch Statements

import (
	"fmt"
	"time"
)

func main() {
	switch dayBorn := time.Saturday; {
	case dayBorn == time.Saturday || dayBorn == time.Sunday:
		fmt.Println("You born on weekend")
	default:
		fmt.Println("You born on weekday")
	}
}

// · Exercise 2.08: Using the for i Loop

package main

import (
	"fmt"
)

func main() {
	for i := 1; i <= 10; i++ {
		fmt.Println("value of i:", i)
	}
}

// · Exercise 2.09: Looping Over Arrays and Slice

package main

import (
	"fmt"
)

func main() {
	names := []string{"anibal", "didi", "lavida", "misma"}
	for i := 0; i < len(names); i++ {
		fmt.Println("Name is:", i+1, names[i])
	}
}
// · Exercise 2.10: Looping Over a Map

package main

import (
	"fmt"
)

func main() {
	config := map[string]string{
		"debug":    "1",
		"logLevel": "warn",
		"version":  "1.2.1",
	}
	for key, value := range config {
		fmt.Println(key, "=", value)
	}
}

// · Activity 2.02: Looping Over Map Data Using range

package main

import (
	"fmt"
)

func main() {
	words := map[string]int{
		"Gonna": 3,
		"You":   3,
		"Give":  2,
		"Never": 1,
		"Up":    4,
	}
	keyUp := ""
	valueUp := 0
	for key, value := range words { // repeat → :=
		if valueUp < value {
			valueUp = value
			keyUp = key
		}
	}
	fmt.Println("Most Popular Word:", keyUp)
	fmt.Println("With a count of:", valueUp)
}


// · Exercise 2.11: Using break and continue to Control Loops

package main

import (
	"fmt"
	"math/rand"
)

func main() {

	for {
		r := rand.Intn(8)
		if r%3 == 0 {
			fmt.Println("Skip")
			continue
		} else if r%2 == 0 {
			fmt.Println("Stop")
			break
		}
		fmt.Println(r)
	}
}

// · Activity 2.03: Bubble Sort

package main

import (
	"fmt"
)

func main() {
	nums := []int{5, 8, 2, 4, 0, 1, 3, 7, 9, 6}
	fmt.Println("Before:", nums)
	for swapped := true; swapped; {
		swapped = false
		for i := 1; i < len(nums); i++ {
			if nums[i-1] > nums[i] {
				nums[i], nums[i-1] = nums[i-1], nums[i]
				swapped = true
			}
		}
	}
	fmt.Println("After:", nums)

}

// ·


// ·


// ·


// ·


// ·


// ·


// ·

```




