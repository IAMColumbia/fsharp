
# Table of Contents

1.  [FSharp notes](#orgbd15df0)
    1.  [Basics](#org178fc15)
        1.  [Variables, Functions.. both?](#org667b318)
        2.  [Functions](#org3fda44d)
        3.  [Pattern Matching](#org7621529)
    2.  [Simple program](#org57ad55a)
    3.  [Lets do the internet](#org9c97557)
    4.  [Data?](#orgee8b5f0)
    5.  [Dockerizing everything](#org2cf693d)


<a id="orgbd15df0"></a>

# FSharp notes


<a id="org178fc15"></a>

## Basics


<a id="org667b318"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think of it as a function, functions cannot be reassigned and you cant have 2 with the same signature. Comparing variables gets a little weird as well since we use the single &rsquo;=&rsquo; for both assignment and value comparison

    let x = 10
    println x = 10 // prints true

If we need a variable that can be changed, which is rarer than you think, you have to use the &ldquo;mutable&rdquo; keyword

    let mutable x = 10
    x <- x + 1


<a id="org3fda44d"></a>

### Functions

Defining a function in F# is the same as defining a variable, since as discussed above, they are essentially the same thing.

    let square x = x * x

You will find function definitions are very close to your math function notation $f(x) = x*x$. The biggest thing to get used to in F# is type inference. You almost never have to specify a type for a function. The biggest reason to use a type directive in F# is to use an object type (C# Type) so you can access the members of that object

    let len (s : string) = s.length()

Functions can also be nested to do sub calculations

    let evens list =
        let even x = x % 2 = 0
    
        List.filter list even

\`List.filter\` is a system function to filter a list and it takes 2 arguments: a list and a function that returns a boolean $int\RightArrow boolean$, passing a function as an argument (or returns a function as the return type) is known as a &ldquo;higher order function&rdquo; and is a core principle of functional programming

1.  Partial Application

2.  Composition

3.  Currying

4.  Pipes


<a id="org7621529"></a>

### Pattern Matching


<a id="org57ad55a"></a>

## Simple program


<a id="org9c97557"></a>

## Lets do the internet


<a id="orgee8b5f0"></a>

## Data?


<a id="org2cf693d"></a>

## Dockerizing everything

