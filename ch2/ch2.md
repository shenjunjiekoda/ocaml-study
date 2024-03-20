# Chapter 2.

## Basics for OCaml programming

We use `utop` to write and run OCaml code.

Use `;;` to end a line of code and let the OCaml know that it should evaluate the expression.

## expressions

```ocaml
utop # 50 * 50;;
- : int = 2500
```

Phrase `50 * 50` is an expression that multiplies `50` by `50` and returns the result, which is `2500`. The result is of type `int`.

```ocaml
# let x = 50;;
val x : int = 50
# x * x;;
- : int = 2500
```

Note that the variable `x` is not a variable as in other programming languages, but a name that refers to the value `50`.

Phrase `x * x` is an expression that multiplies the value of `x` by itself, which is `50 * 50 = 2500`. The result is also `2500`.

```ocaml
# let x = 50 in x * x;;
- : int = 2500
```

The same result can be obtained using a `let` binding and the `in` keyword.

```ocaml
# let a = 1 in 
  let b = 2 in 
    a + b;;
- : int = 3
```

This code is just one expression that adds `1` and `2` and returns the result, which is `3`. The result is of type `int`.

We can also define a function that returns the square of a number:

```ocaml
# let square x = x * x;;
val square : int -> int = <fun>
# square 50;;
- : int = 2500
```

The function `square` takes an integer argument `x` as input and returns its evalation result of square, which is `x * x`. We can call this function with the argument `50` and get the result `2500`.

Now, we want to know the even-odd nature of the square. We can define a function `even` that returns `true` if a number is even and `false` if it is odd:

```ocaml
# let square_is_even x = square x mod 2 = 0;;
val square_is_even : int -> bool = <fun>
# square_is_even 3;;
- : bool = false
# square_is_even 4;;
- : bool = true
```

Notice the type OCaml infers for the function `square_is_even`. It is `int -> bool`, which means that it takes an integer argument and returns a boolean value.

A function may take multiple arguments, separated by spaces, without parentheses and commas:
```ocaml
# let ordered a b c = 
  a <= b && b <= c;;
val ordered : int -> bool = <fun>
# ordered 1 2 3;;
- : bool = true
# ordered 1 3 2;;
- : bool = false
```

Another example of a function that takes multiple float arguments:
```ocaml
# let average x y = (x +. y) /. 2.;;
val average : float -> float -> float = <fun>
# average 1. 2.;;
- : float = 1.5
```

In other languages(such as C) integers get promoted to floats when used in arithmetic operations. For example, `1 + 2.5` in C would result in `3.5`, but in OCaml it would be a type error. The `+` operator in OCaml needs two integers to be used for addition.
