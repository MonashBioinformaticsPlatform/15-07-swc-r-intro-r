---
layout: page
title: Programming with R
subtitle: Reference
---

## Basic Operation

- `# this is a comment in R`
- Use `x <- 3` to assign a value, `3`,  to a variable, `x`
- R counts from 1, unlike many other programming languages (e.g., Python)
- `c(value1, value2, value3)` creates a vector
- `length(vec)` returns the number of elements contained in the variable
  `vec`, if it is a vector.
- `vec[i]` selects the i'th element from the variable `vec`, if it is a vector.
- `mat[i,j]` selects the cell at the i'th row and j'th column of `mat`, if `mat` is a matrix or data frame.

- `print(thing)` print the variable `thing` to the console.
- `cat(thing1, thing2, "\n")` another more flexible way to print things. `"\n"` is the "newline" character, it means start a new line of output.

- `?name` get help on the function called `name`


## Data types and structures

What you can do with an object largely depends on what "type" it is.

Check what type of thing you are dealing with:
`class(x)`

- "numeric", "character", "factor", "integer", "logical" - Vectors, containing a list of things all of the same basic type. In R, a single value is a vector with length 1.

- "matrix" - Matrices, a tabular 2D data structure, elements are all of the same basic type.

- "list" - A list of things. Unlike vectors, lists can contain different types of things, and can contain other container data structures. If a function needs to return several different things of different types, a list is a great container to put them all in.

- "data.frame" - Another tabular 2D data structure. A sequence of records (rows), each having certain attributes (columns). Each column is all the same type of thing, but different columns can contain different types of thing. You could think of a data.frame as a *list* of column *vectors*.

Insist that a thing have a certain type:
`as.vector(x)`
`as.matrix(x)`
`as.data.frame(x)`


## Control Flow

- create a `for` loop to process elements in a collection one at a time

        for (i in 1:5) {
          print(i)
        }

    This will print:

        1
        2
        3
        4
        5

- Create a contitional using `if`, `else if`, and `else`

		if (x > 0) {
			print("value is positive")
		} else if (x < 0) {
			print("value is negative")
		} else{
			print("value is neither positive nor negative")
		}


- equal: Use `==` to test for equality
    - `3 == 3`, will return `TRUE`,
    - `'apple' == 'orange'` will return `FALSE`

- not-equal: Use `!=` to test for non-equality
    - `3 != 3` will return `FALSE`
    - `'apple' != 'orange'` will return `TRUE`

- other comparisons: `<`, `>`, `<=`, `>=`  

- and: `X & Y` is `TRUE` if both X and Y are true

- or: `X | Y` is `TRUE` if either X or Y, or both are true

- not: `!X` is `TRUE` if X is `FALSE` and vice versa


## Functions

- Defining a function:

        is_positive <- function(value) {
            if (value > 0) {
                return(TRUE)
            } else {
                return(FALSE)
            }
        }

- Use `return` to return a value. (Alternatively, in R, the last executed line of a function is automatically returned.)

- Specifying a default value for a function argrment

		increment_me <- function(value_to_increment, value_to_increment_by = 1) {
			return(value_to_increment + value_to_increment_by)
		}

    `increment_me(4)` will return 5

    `intrement_me(4, 6)` will return 10

- Call a function by using `function_name(function_arguments)`

- The apply family of functions are sometimes useful as an alternative to `for` loops:

    `apply()`
    `sapply()`
    `lapply()`
    `mapply()`

    `apply(dat, MARGIN = 2, mean)`
    will return the average (`mean`) of each column in `dat`

## .R files

- Run all the code in a .R file with

    `source("filename.R")`

- From bash, run a .R file with

    `Rscript filename.R`


## Packages
- Install package by using `install.packages("package-name")`
- Update packages by using `update.packages("package-name")`
- Load packages by using `library("package-name")`

## Glossary

argument
:   A value given to a function or program when it runs. The term is often used interchangeably (and inconsistently) with [parameter](#parameter).

call stack
:   A data structure inside a running program that keeps track of active function calls. Each call's variables are stored in a [stack frame](#stack-frame); a new stack frame is put on top of the stack for each call, and discarded when the call is finished.

comma-separated values (CSV)
:   A common textual representation for tables in which the values in each row are separated by commas.

comment
:   A remark in a program that is intended to help human readers understand what is going on, but is ignored by the computer. Comments in Python, R, and the Unix shell start with a `#` character and run to the end of the line; comments in SQL start with `--`, and other languages have other conventions.

conditional statement
:   A statement in a program that might or might not be executed depending on whether a test is true or false. In R, these are `if` statements.

documentation
:   Human-language text written to explain what software does, how it works, or how to use it.

for loop
:   A loop that is executed once for each value in some kind of set, list, or range. See also: [while loop](#while-loop).

function body
:   The statements that are executed inside a function.

function call
:   A use of a function in another piece of software.

function composition
:   The immediate application of one function to the result of another, such as `f(g(x))`.

index
:   A subscript that specifies the location of a single value in a collection, such as a single pixel in an image.

loop variable
:   The variable that keeps track of the progress of the loop.

notional machine
:   An abstraction of a computer used to think about what it can and will do. Your "mental model".

parameter
:   A variable named in the function's declaration that is used to hold a value passed into the call. The term is often used interchangeably (and inconsistently) with [argument](#argument).

pipe
:   A connection from the output of one program to the input of another. When two or more programs are connected in this way, they are called a "pipeline".

return statement
:   A statement that causes a function to stop executing and return a value to its caller immediately.

shape (of an array)
:   An array's dimensions, represented as a vector. For example, a 5&times;3 array's shape is `(5,3)`. In R we get the shape of a matrix or data frame with `dim`, and the length of a vector with `length`.

silent failure
:   Failing without producing any warning messages. Silent failures are hard to detect and debug.

slice
:   A regular subsequence of a larger sequence, such as the first five elements or every second element.

stack frame
:   A data structure that provides storage for a function's local variables. Each time a function is called, a new stack frame is created and put on the top of the [call stack](#call-stack). When the function returns, the stack frame is discarded.

standard input (stdin)
:   A process's default input stream. In interactive command-line applications, it is typically connected to the keyboard; in a [pipe](#pipe), it receives data from the [standard output](#standard-output) of the preceding process.

standard output (stdout)
:   A process's default output stream. In interactive command-line applications, data sent to standard output is displayed on the screen; in a [pipe](#pipe), it is passed to the [standard input](#standard-input) of the next process.

string
:   Short for "character string", a [sequence](#sequence) of zero or more characters. In R, this is the "character" data type.

while loop
:   A loop that keeps executing as long as some condition is true. See also: [for loop](#for-loop).
