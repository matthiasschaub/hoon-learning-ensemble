# Urbit

A new kind of computer that you can own completely in ways that matter:

networking, identity, and data.


# Urbit

1. A complete stack for personal computing in the cloud.

2. A network between the nodes that run that stack.


# Urbit

1. Urbit OS - System Protocol

2. (Urbit ID - Identity Protocol)


# Urbit OS

A clean-slate OS.

A single pure function.


# (Urbit ID)

(A peer-to-peer end-to-end-encrypted network.)

(A decentralized addressing and public key infrastructure.)


# Ship

```bash
./urbit -F zod  # boot an instance of a fakeship
./urbit zod     # if already boot run using
```


# Hoon

A statically typed, functional programming language.

(Hoon compiles to Nock.)


# Nock

A set of 12 operation codes (which fit on a t-shirt).

A purely functional typeless programming language.


# Nock

*Nock* is machine code designed for machines to run.

*Hoon* is a programming language designed for people to use.


# Noun

Everything in Hoon (and Nock, and Urbit) is a *noun*.

A noun is an atom or a cell.
An atom is any natural number.
A cell is any ordered pair of nouns.


# Noun

A Binary tree whose leaves are atoms.

```
        [5 9]
          .
         / \
        5   9

    [[1 2] [3 4]]
          .
         / \
        /   \
       /     \
      .       .
     / \     / \
    1   2   3   4
```


# Noun

Utilized in three different manners:

1. formulas
2. subjects
3. products

A *formula* is a noun utilized as a function
that takes in a noun, its *subject*,
and returns a noun, its *product*.

```
subject  ->  formula  ->  product
             (Nock 0)
[5 9]    ->  [0 3]    ->  9
```


# Nock

```hoon
::  subject  formula
.*  [5 9]    [0 3]    :: evaluate with Nock 2

.*  1        [4 0 1]  :: increment
```


# Hoon Runes

A way to form expressions (statements/keywords).

Fundamental operators.

If nouns are nouns, runes are verbs.


# Runes

Made out of two ASCII special characters.

```hoon
.+  1               :: increment with Nock 4
```


# Runes

Runes take a fixed number of children.

```hoon
:-  5  9            :: construct cell (two-tuple)

  :-                :: pseudo syntax
 /  \
5    9

[5 9]               :: syntactic sugar
```


# Runes

A child can be another rune.

Chain runes until a value is arrived at.

```hoon
.=  3  .+  2        :: increment and test for equality
```


# Runes

```hoon
%-  add  :-  5  9   :: call function

        %-          :: pseudo syntax
       /  \
     add   :-
          /  \
         5    6
```


# Subject

Where does `add` come from?


# Subject

The subject refers to the parent binary tree of an expression and serves
as state, lexical scope, environment, and function argument.

```hoon
:: current subject
.
```


# Subject

```hoon
::  the product of `q`,
::  with the product of `p`
::  taken as the subject.
::  =>  p  q
=>  9  .
=>  .  %-  add  :-  5  9      :: current (dojo subject) as subject
=>  %foo  %-  add  :-  5  9   :: will fail
```


# Subject

What is the subject of `add`?


# Core

A pattern to store code as data.

A pair of code and data: `[code data]`

```hoon

    core
   /    \
code    data
 ```


# Core

```hoon
%-  head  add  :: code
%-  tail  add  :: data
```


# Core

```hoon
:: [[sample context]
:: <list of arms.hash rendered as text>
[[a=0 b=0] <33.rnj 1.pnw %139>]
```


# Core

Core stores code in named adressess called arms
in the left side of the binary tree.

Then it stores the whole subject that it was build against
in the right side of the binary tree

```hoon
=>
|%                          :: produce a core, `[code data]`
++  increment-100  .+  100  :: produce an arm
--                          :: end of core
increment-100               :: evaluate code at named adressess
```
