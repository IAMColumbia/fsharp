
# Table of Contents

1.  [FSharp notes](#orga54dbd7)
    1.  [Basics](#org8c0fc3c)
        1.  [Variables, Functions.. both?](#org384ec6e)
        2.  [Functions](#orgba8382c)
    2.  [Simple program](#org670ef72)
    3.  [Lets do the internet](#org3853e0c)
    4.  [Data?](#org73ee485)
    5.  [Dockerizing everything](#orgcee8859)


<a id="orga54dbd7"></a>

# FSharp notes


<a id="org8c0fc3c"></a>

## Basics


<a id="org384ec6e"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think of it as a function, functions cannot be reassigned and you cant have 2 with the same signature. If we need a variable that can be changed, which is rarer than you think, you have to use the &ldquo;mutable&rdquo; keyword

    let mutable x = 10
    x <- x + 1


<a id="orgba8382c"></a>

### Functions

Defining a function in F# is the same as defining a variable, since as discussed above, they are essentially the same thing.

    let square x = x * x

You will find function definitions are very close to your math function notation $f(x) = x*x$.


<a id="org670ef72"></a>

## Simple program


<a id="org3853e0c"></a>

## Lets do the internet


<a id="org73ee485"></a>

## Data?


<a id="orgcee8859"></a>

## Dockerizing everything

