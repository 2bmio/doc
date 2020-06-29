---
title: Variables and Operators
description: 
published: true
date: 2020-06-29T15:20:56.675Z
tags: 
editor: markdown
---

# anki

slices, arrays, and maps

Here, we're declaring a global variable, which is a list of strings, and initializing it with data. The text or strings in Go support multi-byte UFT-8 encoding, making them safe for any language. The type of list we're using here is called a slice. There are three types of lists in Go: slices, arrays, and maps. All three are collections of keys and values, where you use the key to get a value from the collection. Slice and array collections use a number as the key. The first key is always 0 in slices and arrays. Also, in slices and arrays, the numbers are contiguous, which means there is never a break in the sequence of numbers. With the map type, you get to choose the key type. You use this when you want to use some other data to look up the value in the map.


When you declare a variable, it needs four things:


Operators:

While variables hold the data for your application, they become truly useful when you start using them to build the logic of your software. Operators are the tools you use to work with your software's data. With operators, you can compare data to other data. For example, you can check whether a price is too low or too high in a trading application. You can also use operators to manipulate data. For example, you can use operators to add the costs of all the items in a shopping cart to get the total price.

Arithmetic operators
  Shorthand Operators
Comparison operators
	True if
  	==
    !=
    >=
    <=
    <
    >
Logical operators
	True if
		&&
    ||
    !
Address operators
Receive operators

Zero Values
fmt.Printf to expose more detail about the values


Getting a Pointer
To get a pointer, you have a few options. You can declare a variable as being a pointer type using a var statement. You can do this by adding an * at the front of most types. This notation looks like var <name> *<type>. The initial value of a variable that uses this method is nil. You can use the built-in new function for this. This function is intended to be used to get some memory for a type and return a pointer to that address. The notation looks like <name> := new(<type>). The new function can be used with var too. You can also get a pointer from an existing variable using &. This looks like <var1> := &<var2>.
  
  
######################################

  
```go
 func main() {
	rand.Seed(time.Now().UnixNano())
	r := rand.Intn(5) + 1
	stars := strings.Repeat("*", r)
	fmt.Println(stars)
}

////////////  

var (
	debug       bool      = true
	logLevel    string    = "info"
	startUpTime time.Time = time.Now()
)

func main() {
	fmt.Println(debug, logLevel, startUpTime)
}

////////////

var (
	debug       = false
	logLevel    = "info"
	startUpTime = time.Now()
)

func main() {
	fmt.Println(debug, logLevel, startUpTime)
}


////////////  
func main() {
	// debug := true
	// logLevel := "info"
	// startUpTime := time.Now()

	debug, logLevel, startUpTime := true, "info", time.Now()

	fmt.Println(debug, logLevel, startUpTime)
}


////////////

func getConfig() (bool, string, time.Time) {
	return true, "info", time.Now()
}

func main() {
	debug, logLevel, startUpTime := getConfig()
	fmt.Println(debug, logLevel, startUpTime)
}


////////////  
  
var defOffSet = 10

func main() {
	offset := defOffSet
	fmt.Println(offset)

	offset += defOffSet
	fmt.Println(offset)
}

////////////  
func main() {
	query, limit, offset := "bat", 10, 0
	query, limit, offset = "ball", offset, 20
	fmt.Println(query, limit, offset)
}

////////////    
func main() {
	var total float64 = 2 * 13
	fmt.Println("Sub: ", total)
	total = total + (4 * 2.25)
	fmt.Println("Sub: ", total)
	total = total - 5
	fmt.Println("Sub: ", total)
	tip := total * .1
	fmt.Println("Tip: ", tip)
	total = total + tip
	fmt.Println("Total: ", total)
	split := total / 2
	fmt.Println("Split: ", split)
	visitCount := 24
	visitCount = visitCount + 1
	remainder := visitCount % 5
	if remainder == 0 {
		fmt.Println("Whit this visit, you've earned a rewards")
	}
}
////////////  
func main() {
	count := 5
	count += 5
	count++
	fmt.Println(count)
	count--
	fmt.Println(count)
	count -= 5
	fmt.Println(count)
	name := "Jonh"
	name += " Smith"
	fmt.Println("Hello,", name)
}

////////////

func main() {
	visits := 15
	fmt.Println("Fist visit :", visits == 1)
	fmt.Println("Return visit: ", visits != 1)
	fmt.Println("Silver member: ", visits > 10 && visits < 20)
	fmt.Println("Golden member: ", visits >= 20 && visits < 30)
	fmt.Println("Platinum member: ", visits >= 30 && visits < 35)
}

////////////
  
func main() {
	var count int
	fmt.Printf("Count: %#v \n", count)
	var discount float64
	fmt.Printf("Discount: %#v \n", discount)
	var debug bool
	fmt.Printf("Debug: %#v \n", debug)
	var message string
	fmt.Printf("Message: %#v \n", message)
	var emails []string
	fmt.Printf("Emails: %#v \n", emails)
	var startTime time.Time
	fmt.Printf("Start %#v \n", startTime)
}

////////////    

func main() {
	var count1 *int
	count2 := new(int)
	countTemp := 5
	count3 := &countTemp
	t := &time.Time{}

	if count1 != nil {
		fmt.Printf("Count 1: %#v\n", *count1)
	}
	if count2 != nil {
		fmt.Printf("Count 2: %#v\n", *count2)
	}
	if count3 != nil {
		fmt.Printf("Count 3: %#v\n", *count3)
	}
	if t != nil {
		fmt.Printf("Time: %#v\n", *t)
		fmt.Printf("Time: %#v\n", t.String())
	}
}
////////////
func main() {
	var count int
	add5Value(count)
	fmt.Println("add5value post: ", count)
	add5Point(&count)
	fmt.Println("add5Point post: ", count)
}

func add5Value(count int) {
	count += 5
	fmt.Println("add5Value: ", count)
}

func add5Point(count *int) {
	*count += 5
	fmt.Println("add5Point: ", *count)
}

////////////

const globalLimit = 100
const maxCacheSize = 10 * globalLimit

const (
	cacheKeyBook = "book_"
	cacheKeyCD   = "cd_"
)

var cache map[string]string

func cacheGet(key string) string {
	return cache[key]
}

func cacheSet(key, val string) {
	if len(cache)+1 >= maxCacheSize {
		return
	}
	cache[key] = val
}

func getBook(isbn string) string {
	return cacheGet(cacheKeyBook + isbn)
}

func setBook(isbn string, name string) {
	cacheSet(cacheKeyBook+isbn, name)
}

func getCD(sku string) string {
	return cacheGet(cacheKeyCD + sku)
}

func setCD(sku string, title string) {
	cacheSet(cacheKeyCD+sku, title)
}

func main() {
	cache = make(map[string]string)
	setBook("1234-5678", "Get Ready To Go")
	setCD("1234-5678", "Get Ready To Go Audio Book")
	fmt.Println("Book:", getBook("1234-5678"))
	fmt.Println("DC:", getCD("1234-5678"))
}

////////////

func main() {

	firstName := "Bob"
	lastName := "Smith"
	age := 34
	peanutAlergy := false

	fmt.Println(firstName)
	fmt.Println(lastName)
	fmt.Println(age)
	fmt.Println(peanutAlergy)
}

////////////

func main() {
	a, b := 5, 10
	fmt.Println(a == 10, b == 5)
	fmt.Println("orig value of A is:", a, "\norig value of B is:", b)

	swap(&a, &b) // core
	fmt.Println(a == 10, b == 5)
}

func swap(a *int, b *int) {
	*a, *b = *b, *a //core
	fmt.Println("swap value of A:", *a, "\nswap value of B:", *b)
}
                                                 ////////////
func main() {
	message := ""
	count := 5
	if count > 5 {
		message = "Greater than 5"
	} else {
		message = "No greater than 5"
	}
	fmt.Println(message)
}
////////////
func main() {
	count := 0
	if count < 5 {
		count = 10
		count++
	}
	fmt.Println(count == 11)
}
```
  
  
  
  
  

