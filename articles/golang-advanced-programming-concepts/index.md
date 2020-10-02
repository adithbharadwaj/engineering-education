
*Go is a powerful statically-typed, open-source, and procedural programming language that is gaining popularity in the IT industry*. In the [first article](/engineering-education/golang-part-1-introduction/), we looked at the history of Go, its purpose, and its installation. In the [second article](/engineering-education/golang-part-2-programming-basics/), we explored basic programming concepts such as variables, input/output, etc.., In this article, we are going to go over advanced programming concepts such as functions, structures, and arrays.

### Table of Contents

- [Functions](#functions)
- [Arrays](#arrays)
- [Structures](#structures)
- [Putting It All Together](#putting-it-all-together)
- [Further Reading](#further-reading)

### Functions

A [function](https://www.tutorialspoint.com/computer_programming/computer_programming_functions.htm) can be defined as a set of reusable code that can be used to perform a particular task based on the requirements of the user. In other words, if there are a lot of repetitive tasks in the program, the user can create a function for that particular task. They execute the function instead of writing the same piece of code multiple times. By creating functions, the user can avoid repetitive code and make the program easier to read and understand. By grouping similar tasks, the code becomes more [modular](https://en.wikipedia.org/wiki/Modular_programming) and more intuitive to other developers. It thereby increasing productivity and efficiency in the team. Therefore, functions are extremely powerful, and it is generally considered good practice to use functions in your program. 

The syntax for creating functions in Go is as follows:

```go
func <name of function>(list of arguments) return type{
	// block of reusable and repetitive code
        return statement
}
```

Let us create a function to add two numbers and return the result.

```go
package main

import "fmt"

func add_numbers(x int, y int) int {
    return x + y
}

func main() {
    var x = add_numbers(1, 2)
    fmt.Println(x)
}
```

The function `add_numbers()` takes 2 parameters: the two numbers to be added, and returns the sum of the two numbers. The two numbers are specified as `int` in the above example, but the parameters can be of any data type permissible in Go. The return type is also specified as int because the sum of two integers is also an integer.  

A function can be ["called"](https://www.digitalocean.com/community/tutorials/how-to-define-and-call-functions-in-go) or "invoked" by specifying the name of the function and passing the required parameters. In the above example, we call the `add_numbers()` function by passing two integers as parameters.  

The `main()` function is a special type of function. It serves as the entry point to the program where all other functions and pieces of code are executed. Go automatically runs the `main()` function and the program ends when we reach its end. Therefore, there is no need to explicitly invoke or call the main function.

### Arrays

An [array](https://www.geeksforgeeks.org/arrays-in-go/) is a collection of multiple values or items of the same data type. This makes it easier to find a value by referencing its position relative to the start of the array (index 0). In other words, if there are 10 items of the same data type numbered from 0 to 9 (array indexes always start from 0), we can get the 6th item by simply looking at index 5 in the array. For example, if the user wants to store the scores obtained by 100 students in a test, he can use an integer array of length 100. 

The syntax for creating an array is as follows:

```go
var <name of the array>[<length>] <data type>

```

Example:

```go
package main

import "fmt"

func main() {
    var test[10] int
        // assigning the value 10 to the first index in the array
    test[0] = 10
        // assigning the value 20 to the second index
    test[1] = 20
        // printing the first element
    fmt.Println(test[0])

    var test2[1] string
    test2[0] = "hello"
    fmt.Println(test2[0])
}
```

In the above example, we create an array of integers called "test" with a length of 10. We then assign the values 10 and 20 to the first and second index, respectively. We can retrieve and print the first value by referring to the index 0. 

```go
package main

import "fmt"

func main() {
    var test[10] int
    for i: = 0; i < 10; i++ {
        test[i] = i
    }

    for i: = 0; i < 10; i++ {
        fmt.Println(test[i])
    }
}
```

We can also use loops to assign values to the array. In the above example, we assign values from 0 to 9 to the elements in the array and then print them on the screen.

### Structures

A [structure](https://medium.com/rungo/structures-in-go-76377cc106a2), also called struct, is similar to a [class](https://en.wikipedia.org/wiki/Class_(computer_programming)) in the [object-oriented](https://searchapparchitecture.techtarget.com/definition/object-oriented-programming-OOP) paradigm. For those that are not familiar with OOP or object-oriented programming, structs are user-defined types that are used to group similar fields of the same or different data types together. For instance, details about a student such as his name, score, age, etc. are values of different data types. It makes sense to group them instead of creating different variables for each of them.  

The syntax for creating a struct is as follows:

```go
type <name of the structure> struct {
    field1 <data type>
    field2 <data type>
}
```

Example:

```go
package main

import "fmt"

type Student struct {
    name string
    age int
    score float64
}

func main() {
    var s1 = Student {
        "Adith", 1, 99.5
    }
    fmt.Println(s1)
    fmt.Println(s1.name)
    fmt.Println(s1.age)
    fmt.Println(s1.score)

    var s2 = Student {}
    s2.name = "Bharadwaj"
    fmt.Println(s2.name)
}
```

In the above example, we create a struct called "Student" with three fields: `name`, `age`, and `score` of types `string`, `int`, and `float64`, respectively. In the main function, we create a variable called `s1` of type `Student` and initialize it with values that correspond to the `name`, `age`, and `score`. The curly braces({}) are used to initialize the values of a struct. 

The `dot(.)` operator can also be used to assign values to the fields in the struct. In the example above, we create another variable called `s2` of type `Student` without initializing it. We then use the `dot(.)` operator to assign the value "Bharadwaj" to the name.

### Putting it all together

We are going to write a program to create a `struct` called "Student", get the details of 5 students, and display them to the user.

```go
package main

import "fmt"

type Student struct {
    name string
    age int
    score float64
}

func get_details() {

    var array[5] Student
    fmt.Println("Enter the details of 5 students")

    for i: = 0; i < 5; i++ {
        fmt.Println("Enter the name: ")
        fmt.Scanln( & array[i].name)
        fmt.Println("Enter the age: ")
        fmt.Scanln( & array[i].age)
        fmt.Println("Enter the score: ")
        fmt.Scanln( & array[i].score)
    }

    fmt.Println("The details of the 5 students are as follows: ")
    for i: = 0; i < 5; i++ {
        fmt.Println("Name:", array[i].name)
        fmt.Println("Age: ", array[i].age)
        fmt.Println("Score: ", array[i].score)
    }
}

func main() {
    get_details()
}
```

The function `get_details()` gets the details of 5 students from the user and displays them on the terminal using a `for` loop. We create an array of type Student with length 5. This array stores the details of all 5 students. 

### Further reading

- [Go language specification](https://golang.org/ref/spec)
- [Tour of Go](https://tour.golang.org/basics/1)
- [Go by example](https://gobyexample.com/)
