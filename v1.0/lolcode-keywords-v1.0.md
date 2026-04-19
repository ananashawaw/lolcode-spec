# Keywords

This namespace forms the beginning of a rudimentary language
reference, documenting the known keywords in LOLCODE.

It is a good place for a beginner to get started, as the definitions
are currently minimal stubs. If you feel you have an insight into an
existing keyword, please feel free to extend the definition and sign
your work.

## Statement Syntax

As of [LOLCODE Recommendation v1.0](lolcode-spec-v1.0.md), statements are
terminated by either a `.` or a newline

## List of keyword pages
### BTW
#### Pre-v1.0
```lolcode
BTW <comment>
```

This has been seen to be the most widely accepted form of commenting
on the site. Other options are `^^`, however the added punctuation has
been seen by many as non-LOLCODE-style.


#### LOLCODE Recommendation v1.0
```lolcode
BTW <comment>
```

While this was not explicitly voted upon, it seemed to be taken for
granted. It was the standard used for commenting in examples and has
been adopted by nearly all developers in the developer meeting.  
Hopefully this will be standardized at the next developer meeting.

### BYES
#### LOLCODE Recommendation v1.0
```lolcode
BYES [<code> [<string>]]
```

Causes the program to exit with the specificed status code and
message.  
If a message is specified, it should be output to standard error or
equivalent, and the status code specified should be returned.  
If no message is specified, no message should be output, but if no
code is specified, an implementation-specific success code should be
returned.

See also: [DIAF](#DIAF)

### CAN-HAS
#### Pre-v1.0
Library inclusion. Triggers an error condition if the library is not
found. Consider `require` or `include` for parallels.

#### LOLCODE Recommendation v1.0
```lolcode
CAN HAS <file/module>?
```
Includes the file or loads the module, and dies on error.

### DIAF
#### LOLCODE Recommendation v1.0
```lolcode
DIAF [<code> [<string>]]
```

Causes the program to exit with the specificed status code and
message.  
If a message is specified, it should be output to standard error or
equivalent, and the status code specified should be returned.  
If no message is specified, no message should be output, but if no
code is specified, an implementation-specific error code should be
returned.

### GIMMEH
#### Pre-v1.0
gets input from `STDIN`

#### LOLCODE Recommendation v1.0
```lolcode
GIMMEH [(LINE|WORD|LETTAR)] <VAR> [OUTTA <filedesc>]
```

This inputs a line, word, or character from the specified file
descriptor (currently only `STDIN` is standard).
- Default read type is `LINE` if not specified
- Default file descriptor is `STDIN` if not specified

### GTFO
#### LOLCODE Recommendation v1.0
```lolcode
GTFO
```

This breaks out of the innermost loop. This is equivalent to the
“break” statement in most languages. As of this recommendation, there
is no “continue” statement, though this is planned for the future.

See also: [IM IN YR](#IM-IN-YR)

### HAI
#### Pre-v1.0
Start block

#### LOLCODE Recommendation v1.0
Opens the program. The program block is terminated by a [KTHXBYE](#KTHXBYE).

### I HAS A
#### Pre-v1.0
Variable declaration and initialisation. Variables are untyped, as far as we can tell so far.

#### LOLCODE Recommendation v1.0
```lolcode
I HAS A <var> ITZ ...
```

Declare a variable. Note the following:
- Every variable is an array.
- `ITZ ...` has been reserved for future usage and should not be used
  (except possibly for initialization of single-element arrays)
- At present, all arrays are heterogeneous (they can have different
  types of values in them). This may change in the future!
All values **are** typed, and the types are:
- `NUMBAR` (signed integer, at least 32 bits wide)
- `YARN` (string)
- `ARRAY` (contains NUMBARs and/or YARNs and/or ARRAYs)
Currently the interpreter and/or compiler does type checking at
compile and/or runtime. This may get nailed down to one or the other
in future recommendations.

See [IN MAH](#IN-MAH)

### IM IN YR
#### Pre-v1.0
Start a loop, with a label following. Ends with [IM OUTTA YR](#IM-OUTTA-YR).

#### LOLCODE Recommendation v1.0
```lolcode
IM IN YR [<loop label>]
```

Starts a loop declaration. Notice that the loop label has no effect
(except possibly tracing and debugging). There are no named breaks.  
Note that [IM OUTTA YR](#IM-OUTTA-YR) is NOT the terminator in this
recommendation, [KTHX](#KTHX) is.

See also [KTHX](#KTHX), [GTFO](#GTFO)

### IM OUTTA YR
#### Pre-v1.0
Matched with [IM IN YR](#IM-IN-YR), it ends a loop block.

#### LOLCODE Recommendation v1.0
Deprecated in favor of [KTHX](#KTHX)

### IN MAH
#### LOLCODE Recommendation v1.0
```lolcode
[<key> IN MAH]* <var>
```

This (l-value and r-value) indexes a (multidimensional, if more than
one) array, and currently only positive integral keys are supported.  
While there is no operator precedence defined as of this
recommendation, it is probably best for `IN MAH` to have very high
precedence.  
If this is an l-value (left hand side of an assignment) the array
should be expanded to be at least `<key>` elements in that direction.

```lolcode
a IN MAH b IN MAH c IN MAH var
```

 Would be equivalent to

```C
var[c][b][a]
```

in C, and would expand each “axis” of the array as necessary to fit
that element in. If it is an r-value (that is, being accessed instead
of assigned) and the index is out of the current bounds of the array,
an error should be generated.

If `var` is accessed without an index, it should be operated upon for each element, in most cases.  
See [VISIBLE](#VISIBLE) for a brief discussion of this.

In a future recommendation, there will hopefully be a mechanism for
getting the bounds of an array without having to keep track.

See also: [LOL R](#LOL-R)

### IZ
#### LOLCODE Recommendation v1.0
``` lolcode
IZ <cond>[?]
  [YARLY]
    <atatements>
  [NOWAI
    <statements>]
KTHX
```

This is the recommended syntax for conditional statements (which are
made up of [conditional operators](#Conditional-Operators).  
Note that the `?` is optional, as is the `YARLY...` but the `?`, if
present, must be in the same statement as the conditional, while the
`YARLY` must be its own statement.  
The same goes for `NOWAI`: it has to be its own statement. The `NOWAI` is
equivalent to the else construct, and is only optional if there is no
false branch for the conditional.  
All `IZ` blocks must have a matching [KTHX](#KTHX).

### KTHX
#### LOLCODE Recommendation v1.0
`KTHX` is the closing “bookend” for any block except the [HAI](#HAI)
block. This includes loops, conditionals, functions, etc.  
This is not a “break” style statement.

See also: [KTHXBYE](#KTHXBYE)

### KTHXBYE
#### Pre-v1.0
Block terminator or a break.

#### LOLCODE Recommendation v1.0
Closes [HAI](#HAI) block only. Cannot be used as a break or to close
any other block.

See also: [KTHX](#KTHX)

### LOL R
#### LOLCODE Recommendation v1.0

```lolcode
LOL <l-value> R <expression>
```

Assigns the value of the expression into the l-value (which can be an
element of an array or an array).  
If the l-value is an array with only one element (as it is after just
being created) then the single value of expression should be assigned
to it.

A future recommendation will clarify other options for when this is
not the case.

See also: [I HAS A](#I-HAS-A)

### Operators
#### LOLCODE Recommendation v1.0
##### Conditional Operators
- `BIGR THAN` (>)
- `SMALR THAN` (<)
- `LIEK` ( == )

Notice that these can be modified into the other six conditional
operators with the NOT logical operator. For example, `NOT SMALR THAN`
functionally equivalent to ">=" in most other languages, and `NOT LIEK`
is functionally equivalent to "!=" in other languages.

##### Logical/Bitwise Operators
- `NOT` (! / ~)
- `AND` (&& / &)
- `OR` (|| / |)
- `XOR` (^)

These should be self explanatory. While there is no offical operator
precedence, these should be higher priority than the conditional
operators listed above.

##### Computational Operators
I think the best way to show these is with examples. In them, if b is
stated as "[b]" it is optional, and (as shown in the standard column)
defaults to 1 when not specified.
- `BTW LOLCODE`   : // Standard
- `a UP b`        : a + b
- `UPZ a!![b]`    : a += b (b=1)
- `a NERF b`      : a - b
- `NERFZ a!![b]`  : a -= b (b=1)
- `a TIEMZ b`     : a * b
- `TIEMZD a!![b]` : a *= b (b=1)
- `a OVAR b`      : a / b
- `OVARZ a!![b]`  : a /= b (b=1)

Note that again, while there is no formal recommendation on
prededence, the non-mutating operators (not +=, etc) should have lower
precedence than all other operators, and the mutating should have the
same (very low) precedence as the assignment statement.)

See also: [LOL R](#LOL-R), [I HAS A](#I-HAS-A)

### VISIBLE
#### Pre-v1.0
Print to `STDOUT`

#### LOLCODE Recommendation v1.0
```lolcode
VISIBLE <expression>[!]
```

Prints the value of the expression as concisely as possible (i.e. just
the string, just the number, each element of the array on a separate
line, etc). No newlines (or element separators for an array) are to be
output if the statement ends with a `!`

**Motivation for Array printing**
I think arrays should be printed with a newline delimiting elements
because conceptually, I think calling a command with an array and no
range or single value should execute that command on each individual
argument. Since `VISIBLE`’ing an individual element appends a newline, I
propose that these newlines are maintained.  
The same goes with `!`, except there is no newline, so all array
elements are squashed together with no separator.
