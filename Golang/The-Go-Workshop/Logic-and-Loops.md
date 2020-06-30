---
title: Logic and Loops
description: 
published: true
date: 2020-06-30T13:36:39.265Z
tags: 
editor: markdown
---

# Statements
Your content here

## if / else if / else

```
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
```
for <initial statement>; <condition>; <post statement> {
  <statements>
}

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

// ·


// ·


// ·


// ·


// ·

// ·


// ·


// ·


// ·


// ·


// ·


// ·


// ·

```




