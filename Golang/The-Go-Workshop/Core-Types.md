---
title: 03 - Core Types
description: 
published: true
date: 2020-07-06T19:46:31.341Z
tags: 
editor: markdown
---

# True and False
Your content here



# Numbers

## Integer
## Floating Point
## Overflow and Wraparound
## Big Numbers


# Byte


# Text
## Rune
→ anki → 	pwR := []rune(pw)

# The nil Value



# code
```go

// · Exercise 3.01: Program to Measure Password Complexity

package main

import (
	"fmt"
	"unicode"
)

func passCheck(pw string) bool {
	pwR := []rune(pw)

	if len(pwR) < 8 {
		return false
	}

	hasUpper := false
	hasLower := false
	hasNumber := false
	hasSymbol := false

	for _, v := range pwR {
		if unicode.IsUpper(v) {
			hasUpper = true
		}
		if unicode.IsLower(v) {
			hasLower = true
		}
		if unicode.IsNumber(v) {
			hasNumber = true
		}
		if unicode.IsPunct(v) || unicode.IsSymbol(v) {
			hasSymbol = true
		}
	}
	return hasUpper && hasLower && hasNumber && hasSymbol
}

func main() {
	if passCheck("") {
		fmt.Println("Password good")
	} else {
		fmt.Println("Bad Password")
	}
	if passCheck("1234Abcd?") {
		fmt.Println("Good Password")
	} else {
		fmt.Println("Password is bad")
	}
}

// · Exercise 3.02: Floating-Point Number Accuracy

package main

import (
	"fmt"
)

func main() {
	var a int = 100
	var b float32 = 100
	var c float64 = 100

	fmt.Println("int:", (a/3)*3)
	fmt.Println("float32:", (b/3)*3)
	fmt.Println("float64:", (c/3)*3)
}



// · Exercise 3.03: Triggering Number Wraparound

package main

import (
	"fmt"
)

func main() {
	var a int8 = 125
	var b uint8 = 253

	for i := 1; i < 5; i++ {
		a++
		b++
		fmt.Println(i, ")", "int8", a, "unint8", b)
	}
}


// · Exercise 3.04: Big Numbers

package main

import (
	"fmt"
	"math"
	"math/big"
)

func main() {
	intA := math.MaxInt64
	intA = intA + 1

	bigA := big.NewInt(math.MaxInt64)	// HERE IS THE MAGIC
	bigA.Add(bigA, big.NewInt(1))		// HERE IS THE MAGIC

	fmt.Println("MaxInt64:", math.MaxInt64)
	fmt.Println("Int:", intA)
	fmt.Println("Big Int", bigA.String())

}


// · Exercise 3.05: Safely Looping over a String

package main

import (
	"fmt"
)

func main() {
	content := "AnibaÑsodkk"
	for index, runeVal := range content {
		fmt.Println(index, string(runeVal))
	}
}


// · 

// · 

// · 

// · 

// · 

// · 


```