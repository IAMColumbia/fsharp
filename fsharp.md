
# Table of Contents

1.  [FSharp notes](#org2a953b4)
    1.  [Basics](#orgce83620)
        1.  [Variables, Functions.. both?](#orga750ce7)
        2.  [Functions](#org68ddd41)
        3.  [Pattern Matching](#orga24e89e)
    2.  [Simple program](#org560c022)
    3.  [Lets do the internet](#org85ab464)
    4.  [Data?](#org606c1cc)
    5.  [Dockerizing everything](#orgf11acf0)


<a id="org2a953b4"></a>

# FSharp notes


<a id="orgce83620"></a>

## Basics


<a id="orga750ce7"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think of it as a function, functions cannot be reassigned and you cant have 2 with the same signature. Comparing variables gets a little weird as well since we use the single &rsquo;=&rsquo; for both assignment and value comparison

    let x = 10
    println x = 10 // prints true

If we need a variable that can be changed, which is rarer than you think, you have to use the &ldquo;mutable&rdquo; keyword

    let mutable x = 10
    x <- x + 1


<a id="org68ddd41"></a>

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

    Function composition is a mathematical concept of combining 2 functions into a third function $$f\circ g(x) = f(g(x)$$

3.  Currying

4.  Pipes


<a id="orga24e89e"></a>

### Pattern Matching


<a id="org560c022"></a>

## Simple program


<a id="org85ab464"></a>

## Lets do the internet


<a id="org606c1cc"></a>

## Data?


<a id="orgf11acf0"></a>

## Dockerizing everything

