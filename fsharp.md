
# Table of Contents

1.  [FSharp For CSharp Developers](#orgac2eb7b)
    1.  [Basics](#org384e78c)
        1.  [Variables, Functions.. both?](#org406053d)


<a id="orgac2eb7b"></a>

# FSharp For CSharp Developers


<a id="org384e78c"></a>

## Basics


<a id="org406053d"></a>

### Variables, Functions.. both?

F# is a functional language. Its often joked that <span class="underline">everything</span> is an object in c#. IF that joke was made about f# it would be &ldquo;everything is a function&rdquo;. So when we go to define a variable, which is commonplace in every language, it gets a little bit extra spicy in F#. Variables, under the hood, are functions. Below is the f# equivalent of $f() = 10$

    let x = 10

Calling function &rsquo;x&rsquo; returns 10. \`x\` is immutable, meaning it will always return 10 and cannot be changed. This makes sense if we think

