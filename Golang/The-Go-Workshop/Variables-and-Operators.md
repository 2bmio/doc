---
title: Variables and Operators
description: 
published: true
date: 2020-06-28T14:11:07.800Z
tags: 
editor: markdown
---

# anki

slices, arrays, and maps

Here, we're declaring a global variable, which is a list of strings, and initializing it with data. The text or strings in Go support multi-byte UFT-8 encoding, making them safe for any language. The type of list we're using here is called a slice. There are three types of lists in Go: slices, arrays, and maps. All three are collections of keys and values, where you use the key to get a value from the collection. Slice and array collections use a number as the key. The first key is always 0 in slices and arrays. Also, in slices and arrays, the numbers are contiguous, which means there is never a break in the sequence of numbers. With the map type, you get to choose the key type. You use this when you want to use some other data to look up the value in the map.


```go
package main

import (
	"fmt"
	"math/rand"
	"strings"
	"time"
)

func main() {
	rand.Seed(time.Now().UnixNano())	// time
	r := rand.Intn(5) + 1							// math/rand
	stars := strings.Repeat("*", r)		// strings
	fmt.Println(stars)								// fmt
}
```


