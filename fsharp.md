
# Table of Contents

1.  [FSharp notes](#org83cecf9)
    1.  [Basics](#orga52f082)
        1.  [Variables, Functions.. both?](#orgbb662e3)
        2.  [Functions](#orgdb65419)
    2.  [Types](#org50f6342)
        1.  [Tuples](#org2352f57)
        2.  [Records](#org1d6f214)
        3.  [Discriminated Unions/Algebraic Types](#org4589654)


<a id="org83cecf9"></a>

# FSharp notes


<a id="orga52f082"></a>

## Basics


<a id="orgbb662e3"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think of it as a function, functions cannot be reassigned and you cant have 2 with the same signature. Comparing variables gets a little weird as well since we use the single &rsquo;=&rsquo; for both assignment and value comparison

    let x = 10
    println x = 10 // prints true

If we need a variable that can be changed, which is rarer than you think, you have to use the &ldquo;mutable&rdquo; keyword

    let mutable x = 10
    x <- x + 1


<a id="orgdb65419"></a>

### Functions

Defining a function in F# is the same as defining a variable, since as discussed above, they are essentially the same thing.

    let square x = x * x

You will find function definitions are very close to your math function notation $f(x) = x*x$. The biggest thing to get used to in F# is type inference. You almost never have to specify a type for a function. The biggest reason to use a type directive in F# is to use an object type (C# Type) so you can access the members of that object

    let len (s : string) = s.length()

Using parentheses in this case is fairly straight forward. But it is generally used to write a function that takes in a [tuple](https://en.wikipedia.org/wiki/Tuple)

    let add (a, b) = a + b //function that takes in the tuple (a`, b`)
    let add a b = a + b // function that takes 2 arguments: a and b

Functions can also be nested to do sub calculations

    let evens list =
        let even x = x % 2 = 0
    
        List.filter list even

\`List.filter\` is a system function to filter a list and it takes 2 arguments: a list and a function that returns a boolean, in this case $int\mapsto boolean$. Passing a function as an argument (or returns a function as the return type) is known as a &ldquo;higher order function&rdquo; and is a core principle of functional programming

1.  Partial Application

    Partial application is a cool trick to essentially &ldquo;bake in&rdquo; a function parameter. Instead of default parameters that we get in c-type languages we can use partial application to have constant arguments to functions to make some operations cleaner
    
        let add x y = x + y
        
        let add2 = add 2
        
        let x = add2 2 //x will be 4
    
    in a real world example
    
        let log serverity message = printfn "Severity: %s Message: %s"
        
        let logError = log "Error"
        
        logError "Something Bad Happened"

2.  Composition

    Function composition is a mathematical concept of combining 2 functions into a third function $$f\circ g(x) = f(g(x))$$ $$h = g\circ f$$ $$h(x) = f(g(x))$$
    
    F# uses the &ldquo;>>&rdquo; operator to compose functions and combine them into a new function. Take the following example where we have 2 partial applications of the add function and we compose them together into a third function. Composition is a valuable tool to at least be aware of because it happens all the time under the hood.
    
        let add1 = add 1
        let add2 = add 2
        let add3 = add1 >> add2
        let c = add3 7 // c is 3 + 7

3.  Currying

    Currying and partial application seem to do the same thing but they are slightly different. Currying is taking a function that takes many arguments and turning it into many functions that take 1 argument and then using composition to calculate the final value. Partial application you can choose to use as many or as few arguments for a function wheras currying always uses unary (functions that take one argument) functions.
    
    Our add function $f(a, b) = a + b$ can be written in it&rsquo;s curried form as $a\mapsto b\mapsto a + b$. Currying isnt something we do every day but its essential to know what is happening under the hood as we write more and more complex applications.

4.  Pipes


<a id="org50f6342"></a>

## Types

F# supports a much richer type system than most languages.


<a id="org2352f57"></a>

### Tuples

Tuples are ad-hoc data structures of any number of types

    let pair = (10, 10) //declaring a tuple is just values wrapped in parentheses
    let (x, y) = pair //using pattern matching we can "deconstruct" a tuple into individual values
    let foo = (1, "foo", 12.5) // tuples can mix types


<a id="org1d6f214"></a>

### Records

Records are, essentially, named tuples. Each value in a record has a label that can be used to access the corresponding value

    type Point = { X: float; Y: float; Z: float; }
    let p = { X = 1.0; Y = 2.0; Z = 3.0; } //record expression syntax


<a id="org4589654"></a>

### Discriminated Unions/Algebraic Types

Discriminated unions are special types that can be represented by a different type based on context

    type Shape =
        | Rectangle of width : float * length : float
        | Circle of radius : float
        | Prism of width : float * float * height : float
    
    let rect = Rectangle(length = 1.3, width = 10.0)
    let circ = Circle (1.0)
    let prism = Prism(5., 2.0, height = 3.0)

The most used discriminated union is the \`Option\` type. To cleanly handle a variable that might have a value F# uses the Option type.

    let printValue opt =
        match opt with
        | Some x -> printfn "%A" x
        | None -> printfn "No value."

wrapping a value in an option type and using pattern matching means that you can cleanly handle nulls vs other languages

