
# Table of Contents

1.  [FSharp notes](#org2176a47)
    1.  [Basics](#orgfc4b6ed)
        1.  [Variables, Functions.. both?](#org46940ed)
        2.  [Functions](#org85df4a0)
        3.  [Pattern Matching](#orgdc4455a)
    2.  [Simple program](#org0635091)
    3.  [Lets do the internet](#org24a0c0c)
    4.  [Data?](#orgf37f7df)
    5.  [Dockerizing everything](#org56b0990)


<a id="org2176a47"></a>

# FSharp notes


<a id="orgfc4b6ed"></a>

## Basics


<a id="org46940ed"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think of it as a function, functions cannot be reassigned and you cant have 2 with the same signature. Comparing variables gets a little weird as well since we use the single &rsquo;=&rsquo; for both assignment and value comparison

    let x = 10
    println x = 10 // prints true

If we need a variable that can be changed, which is rarer than you think, you have to use the &ldquo;mutable&rdquo; keyword

    let mutable x = 10
    x <- x + 1


<a id="org85df4a0"></a>

### Functions

Defining a function in F# is the same as defining a variable, since as discussed above, they are essentially the same thing.

    let square x = x * x

You will find function definitions are very close to your math function notation $f(x) = x*x$. The biggest thing to get used to in F# is type inference. You almost never have to specify a type for a function. The biggest reason to use a type directive in F# is to use an object type (C# Type) so you can access the members of that object

    let len (s : string) = s.length()

Functions can also be nested to do sub calculations

    let evens list =
        let even x = x % 2 = 0
    
        List.filter list even

\`List.filter\` is a system function to filter a list and it takes 2 arguments: a list and a function that returns a boolean $int\mapsto boolean$, passing a function as an argument (or returns a function as the return type) is known as a &ldquo;higher order function&rdquo; and is a core principle of functional programming

1.  Partial Application

2.  Composition

3.  Currying

4.  Pipes


<a id="orgdc4455a"></a>

### Pattern Matching


<a id="org0635091"></a>

## Simple program


<a id="org24a0c0c"></a>

## Lets do the internet


<a id="orgf37f7df"></a>

## Data?


<a id="org56b0990"></a>

## Dockerizing everything

