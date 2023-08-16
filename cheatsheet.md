# Cheatsheet

For a version with syntax highlighting see [here](https://talfus-laddus.de/projects/urbit/hoon-learning-ensemble/cheatsheet.html)

## Setup

```bash
$ urbit -F zod  # create fake ship
$ urbit zod     # run fake ship
```

## Dojo (Shell)

```hoon
:dojo|wipe      :: wipe dojo subject
|mount %base    :: create %base folder on earth
```

## Hoon

```hoon
.               :: current subject
a.b.c           :: search path
..arm           :: core in which ++arm is defined
!>(1)           :: cell of type and value
? [1 2]         :: inferred type
```

```hoon
::  nock
.+              :: increment with Nock 4
.=  5  9        :: test for equality
::  cells
:-  5  9        :: construct cell (two-tuple)
[5 9]           :: syntactic sugar for cells
::  calls
%-  add  5  9   :: call a function
::  subject
=>  9  .        :: compose two expressions
=+  n=5         :: pin a value to subject
::  cores
|%              :: produce a core, `[code data]`
  ++  ten  10   :: produce an arm
--              :: end of core
```

## Adresssing

```hoon
    [%a [%b %c]]
         o
       /   \
      /     \
     %a      o
    /  \    / \
   o    o  %b  %c

::  expression   result
+1:[%a [%b %c]]  [%a [%b %c]]
.:[%a [%b %c]]   [%a [%b %c]]

+3:[%a [%b %c]]  %a
-:[%a [%b %c]]   %a

+4:[%a [%b %c]]  [%b %c]
+:[%a [%b %c]]   [%b %c]

+5:[%a [%b %c]]  invalid
-<:[%a [%b %c]]  invalid

+6:[%a [%b %c]]  %b
+<:[%a [%b %c]]  %b

+7:[%a [%b %c]]  %c
+>:[%a [%b %c]]  %c
```

### Examples

```hoon
:: positional addressing (lark notation)
:: - (left) and + (right)
:: alternating with
:: < (left) and > (right)
::
> =tree [[4 5] [6 7]]
> ..tree
[[4 5] 6 7]
> -.tree
[4 5]
> +.tree
[6 7]
> +<.tree
6
> +>.tree
7
```


## Pronounceable runes

```
ace  ' '           ::  spACE
bar  '|'           ::  vertical BAR
bas  '\\           ::  Back Slash (escaped)
buc  '$'           ::  dollars BUCks
cab  '_'           ::  CABoose
cen  '%'           ::  perCENt
col  ':'           ::  COLon
com  ','           ::  COMma
doq  '"'           ::  Double Quote
dot  '.'           ::  dot dot dot ...
fas  '/'           ::  Forward Slash
gal  '<'           ::  Greater Left
gar  '>'           ::  Greater Right
hax  '#'           ::  Hash
hep  '-'           ::  HyPhen
kel  '{'           ::  Curly Left
ker  '}'           ::  Curly Right
ket  '^'           ::  CareT
lus  '+'           ::  pLUS
mic  ';'           ::  seMIColon
pal  '('           ::  Paren Left
pam  '&'           ::  AMPersand pampersand
par  ')'           ::  Paren Right
pat  '@'           ::  AT pat
sel  '['           ::  Square Left
ser  ']'           ::  Square Right
sig  '~'           ::  SIGnature squiggle
soq  '''           ::  Single Quote
tar  '*'           ::  sTAR
tic  '`'           ::  backTiCk
tis  '='           ::  'tis tis, it is
wut  '?'           ::  wut, what?
zap  '!'           ::  zap! bang! crash!!
```

