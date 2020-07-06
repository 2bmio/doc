---
title: 03 - Core Types
description: 
published: true
date: 2020-07-06T18:15:07.678Z
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