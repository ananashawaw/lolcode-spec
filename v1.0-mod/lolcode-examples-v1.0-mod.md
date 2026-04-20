# Table of Contents <!-- :TOC: -->
- [Examples](#examples)
  - [Caturday](#caturday)
    - [On carturday](#on-carturday)
  - [Count 1](#count-1)
    - [COUNT!!1](#count1)
  - [FILEZORZ](#filezorz)
  - [Gimmeh](#gimmeh)
    - [Read Some Input](#read-some-input)
  - [HAI WORLD](#hai-world)
  - [Little Number](#little-number)
    - [IF/THEN/ELSE](#ifthenelse)

# Examples
## Caturday
### On carturday
I'm currently trying to figure out if LOLCODE is adaptable to an event
driven model. I think we could throw a CATURDAY event with the code,
`IZ CATURDAY!`
```lolcode
ON CATURDAY
        IM IN YR BED
                I IZ SLEEPIN!!10
                VISIBLE "Z!"
        KTHX
KTHXBYE
```
So with this code fragment, we have an event block introduced with ON
eventName, and terminated with the usual
[KTHXBYE](lolcode-keywords-v1.0-mod.md#KTHXBYE). We have an effectively
infinite loop, labelled “BED”. The only output is an occasional “Z!”.

## Count 1
### COUNT!!1
```lolcode
HAI
CAN HAS STDIO?
I HAS A VAR
IM IN YR LOOP
        UP VAR!!1
        VISIBLE VAR
        IZ VAR BIGGER THAN 10? KTHXBYE
IM OUTTA YR LOOP
KTHXBYE
```
We've seen
[HAI](lolcode-keywords-v1.0-mod.md#HAI), [KTHXBYE](lolcode-keywords-v1.0-mod.md#KTHXBYE), 
[CAN HAS](lolcode-keywords-v1.0-mod.md#CAN-HAS), and
[VISIBLE](lolcode-keywords-v1.0-mod.md#VISIBLE) already in the listing for
[HAI WORLD](#HAI-WORLD).  We learn a bit about variables in this one.

- Declaration is handled with [I HAS A](lolcode-keywords-v1.0-mod.md#I-HAS-A).
  The (dynamically typed) variable follows.
  - [IM IN YR](lolcode-keywords-v1.0-mod.md#IM-IN-YR) and [IM OUTTA YR](lolcode-keywords-v1.0-mod.md#IM-OUTTA-YR) clearly demarcate a loop construct.
  `LOOP` in this example is simply a label.
- [UP](lolcode-keywords-v1.0-mod.md#Computational-Operators) is an increment
  operator. The (optional, default=1) argument follows `!!`
- The `IZ ... ?`  construct is the basic conditional form. In this
  example, it terminates on the same line with a simple
  [KTHXBYE](lolcode-keywords-v1.0-mod.md#KTHXBYE) command, here used as a
  `BREAK`.
- [BIGGER THAN](lolcode-keywords-v1.0-mod.md#Conditional-Operators) is a comparator.
  
Early consensus from the first irc meeting suggests a slight change
from the original code:
```lolcode
HAI
CAN HAS STDIO?
I HAS A VAR
IM IN YR LOOP
    UPZ VAR!!1
    VISIBLE VAR
    IZ VAR BIGR THAN 10? GTFO. KTHX
KTHX
KTHXBYE
```
Further language features are still pending.

## FILEZORZ
```lolcode
HAI
CAN HAS STDIO?
PLZ OPEN FILE "LOLCATS.TXT"?
        AWSUM THX
                VISIBLE FILE
        O NOES
                INVISIBLE "ERROR!"
KTHXBYE
```
Some notes:

- `PLZ ... ?` introduces a try/exception block.
  - `AWSUM THX` introduces the block to execute on success with `PLZ`.
     It is implicitly closed by...
  - `O NOES`, which is the exception block. It should be closed with
    [KTHX](lolcode-keywords-v1.0-mod.md#KTHX), but it hits the final
    [KTHXBYE](lolcode-keywords-v1.0-mod.md#KTHXBYE), which (I assert) is a
    bit of
     syntactic sugar that closes everything.
- `OPEN` handles non-default-terminal-based I/O. `FILE` in this case is
  simply a variable, a file handle for the LOLCATS.TXT file.
- `INVISIBLE` is a print command to the debug console, commonly known as
  `STDERR`.

## Gimmeh
### Read Some Input
Thanks, ILikePi! (from [input](https://web.archive.org/web/20090111050039/http://lolcode.com/contributions/input))
```lolcode
HAI
CAN HAS STDIO?
I HAS A VAR
GIMMEH VAR
VISIBLE "You said " N VAR N " !!"
KTHXBYE
```
[GIMMEH](lolcode-keywords-v1.0-mod.md#GIMMEH) wins out over `TXT ME A` for inputting a line from the user.

`N` is particularly evil choice for a keyword, I think, but it feels
right as a conjunction, akin to a comma in many other languages. I'm
not keen on adding too many punctuation marks beyond `”`, `!`, and `?`.

## HAI WORLD
```lolcode
HAI
CAN HAS STDIO?
VISIBLE "HAI WORLD!"
KTHXBYE
```
Hello World is pretty much the only way to introduce a language.  
We see four syntax elements in four lines:

[HAI](lolcode-keywords-v1.0-mod.md#HAI) and [KTHXBYE](lolcode-keywords-v1.0-mod.md#KTHXBYE) are the start and stop block delimiters.  
[CAN HAS](lolcode-keywords-v1.0-mod.md#CAN-HAS) is a feature request, like `require` or `include`.  
[VISIBLE](lolcode-keywords-v1.0-mod.md#VISIBLE) is a print statement.

## Little Number
### IF/THEN/ELSE
Okay, I couldn't decide on this one myself, and there were lots of
good suggestions all over the place, but I think we've got something
simple, a modification of [O RLY](https://web.archive.org/web/20090110030446/http://lolcode.com/contributions/o-rly).  
It helps that the various forums that link here called that
construction out as a good one.

```lolcode
HAI
CAN HAS STDIO?
I HAS A VAR
GIMMEH VAR
IZ VAR BIGGER THAN 10?
        YARLY
               BTW this is true
               VISIBLE "BIG NUMBER!"
        NOWAI
               BTW this is false
               VISIBLE "LITTLE NUMBER!"
        KTHX
KTHXBYE
```
See [IZ](lolcode-keywords-v1.0-mod.md#IZ) for more details on the conditional statement.

And let's open up [BTW](lolcode-keywords-v1.0-mod.md#BTW) as the comment form. I'm not closing the door on `^^`, but again, I want to minimize the amount of punctuation.
