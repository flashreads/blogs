---
id: 003-Datatypes_Variables_Constants_in_GO.md
title: Understading Datatypes, Variables Constants In GO
tags:
  - GO
  - Datatypes
  - Variables
  - Constants
author: V Rahul
meta-description: Understading the basic concepts of  Datatypes, Variables Constants In GO language.
date: 2020-10-28 23:46:52 +0530
template: post
categories:
  - go
cover: ../images/categories/go.png
---

# Understading Datatypes, Variables Constants In GO
***
<br>
<br>

## 1. Data Types:
<br>
Data Types represent the type of the value stored in a variable, type of the value a function returns, etc.

There are `three` basic types in Go Language:

`Numeric types` - Represent numeric values which includes integer, floating point, and complex values. Various numeric types are:

int8 - 8 bit signed integers.

int16 - 16 bit signed integers.

int32 - 32 bit signed integers.

int64 - 64 bit signed integers.

uint8 - 8 bit unsigned integers.

uint16 - 16 bit unsigned integers.

uint32 - 32 bit unsigned integers.

uint64 - 64 bit unsigned integers.

float32 - 32 bit floating point numbers.

float64 - 64 bit floating point numbers.

complex64 – has float32 real and imaginary parts.

complex128 - has float32 real and imaginary parts.
<br>
<br>
`String types` - Represents a sequence of bytes(characters). You can do various operations on strings like string concatenation, extracting substring, etc
<br>
<br>

`Boolean types` - Represents 2 values, either true or false.
<br>
<br>

## 2. Variables:
<br>

Variables point to a memory location which stores some kind of value. The type parameter(in the below syntax) represents the type of value that can be stored in the memory location.

Variable can be declared using the syntax-

```
var <variable_name> <type>
```

Once You declare a variable of a type You can assign the variable to any value of that type.

You can also give an initial value to a variable during the declaration itself using


```
var <variable_name> <type> = <value>
```

If You declare the variable with an initial value, Go an infer the type of the variable from the type of value assigned. So You can omit the type during the declaration using the syntax-

```
    var <variable_name> = <value>
```

Also, You can declare multiple variables with the syntax-
```
    var <variable_name1>, <variable_name2>  = <value1>, <value2>
```

The below program in this Go tutorial has some Golang examples of variable declarations-

```

package main
import "fmt"

func main() {
    //declaring a integer variable x
    var x int
    x=3 //assigning x the value 3 
    fmt.Println("x:", x) //prints 3
    
    //declaring a integer variable y with value 20 in a single statement and prints it
    var y int=20
    fmt.Println("y:", y)
    
    //declaring a variable z with value 50 and prints it
    //Here type int is not explicitly mentioned 
    var z=50
    fmt.Println("z:", z)
    
    //Multiple variables are assigned in single line- i with an integer and j with a string
    var i, j = 100,"hello"
    fmt.Println("i and j:", i,j)
}
```
The output will be

```
x: 3
y: 20
z: 50
i and j: 100 hello
```
<br>
<br>

Go Language also provides an easy way of declaring the variables with value by omitting the var keyword using

    <variable_name> := <value>

*Note: You used := instead of =. You cannot use := just to assign a value to a variable which is already declared. := is used to declare and assign value.*

<br>
<br>
Create a file called assign.go with the following code-

```
package main
import ("fmt")

func main() {
	a := 20
	fmt.Println(a)

	//gives error since a is already declared
	a := 30
	fmt.Println(a)
}
```
Execute go run assign.go to see the result as-
```
./assign.go:7:4: no new variables on left side of :=	
```

*Note: Variables declared without an initial value will have of 0 for numeric types, false for Boolean and empty string for strings.*
<br>
<br>

## 3.Constants:

<br>

Constant variables are those variables whose value cannot be changed once assigned. A constant in Go programming language is declared by using the keyword "const".

Create a file called constant.go and with the following code-

```
package main
import ("fmt")

func main() {
	const b =10
	fmt.Println(b)
	b = 30
	fmt.Println(b)
}
```

Execute go run constant.go to see the result as-

```
Execute go run constant.go to see the result as-
```

<br>
<br>
<br>

*That's all for today! Happy Coding :)*