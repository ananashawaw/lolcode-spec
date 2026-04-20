# Table of Contents <!-- :TOC: -->
- [LOLCODE recommendation 1.0](#lolcode-recommendation-10)
  - [Canon](#canon)
  - [UNOFFICIAL](#unofficial)

# LOLCODE recommendation 1.0
HISTORICAL &mdash; 31 May 2007

The following was generated in an IRC meeting as a way of providing a
baseline for implementors. Many of the decisions are being revisited
in [version 1.1](../v1.1/lolcode-spec-v1.1.md) and beyond, through discussion, consensus, and fiat in
the forum.

## Canon
- Statements are separated by `[\n.]+`
- `CAN HAS <module/“file”>?`
  - for inclusion/requirement
- `GIMMEH [(LINE|WORD|LETTAR)] <VAR> [OUTTA <filedesc>]`
  - with default being `LINE` and `STDIN`
- `HAI`
- `KTHXBYE`
  - only closes `HAI` and exits with good condition
- `DIAF [<num> [<text>]]`
  - Exits the program (failure)
  - Status code: `<num>`
  - Printed to stderr or equivalent: `<text>`
- `BYES [<num> [<text>]]`
- `KTHX`
  - is the universal “closing bracket” line
  - for any if block, looping block, function, etc... except `HAI`
- `IM IN YR [<loop label>]`
  - label has no effect
- `VISIBLE <stuff>[!]`
  - prints stuff as minimally as possible and with a newline (unless `!`)
- `I HAS A <l_value> [ITZ ...]`
  - Everything is an array. muahahahaha.
    - To clarify, every VARIABLE is an array,
      and it knows its own dimensions.
  - By default, the variable has one element
  - `ITZ ...` has been tabled for future usage
- `[## IN MAH]* <var>`
  - Since all variables are arrays, with no `IN MAH` it references the
    array as a whole.
  - Multiple occurences of this index sub-levels of the array.
    - `1 IN MAH 2 IN MAH arr` ≡ arr[2][1]
      - `IN MAH` clarifies the dimension of the array itself, it is
        not meant to “return” a smaller array.  
        So, `0 IN MAH 0 IN MAH VAR` must only be used in a
        two-dimensional array, just like `**arr` should only be used
        in a 2D array in C.
  - Does NOT expand the size of the array (except as l_value of assignment)
    - Throws error/dies on out of bounds?
- `LOL <var> R <val>`
  - Assigns value into l_value specified by `<var>`.
  - Extends the size of `<var>` if necessary
  - If no index is specified, applies to all elements? (one by default)
- `IZ <cond> [?] [(.|\n) YARLY] (.|\n) <code> (.|\n) [NOWAI (.|\n) <code>] KTHX`
  - Conditional syntax. [See example](lolcode-examples-v1.0.md#Little-Number)
- Comparison operators: `[NOT] ((BIGR|SMALR) THAN|LIEK)`
  - [See example](lolcode-examples-v1.0.md#Count-1) and [operators](lolcode-keywords-v1.0.md#Conditional-Operators)
- Logical/Bitwise operators: `(NOT|AND|OR|XOR)`
  - [See example](lolcode-examples-v1.0.md#Gimmeh) and [operators](lolcode-keywords-v1.0.md#LogicalBitwise-Operators)
- Operators, (all math, as of v1.0, is integer math)
  - `a UP b` : a +
  - `UPZ a!![b]` : a += b (b=1)
  - `a NERF b` : a - b
  - `NERFZ a!![b]` : a -= b (b=1)
  - `a TIEMZ b` : a * b
  - `TIEMZD a!![b]` : a *= b (b=1)
  - `a OVAR b` : a / b
  - `OVARZ a!![b]` : a /= b (b=1)

## UNOFFICIAL
This stuff was not voted on explicitly but appears to be standard
based on the examples and discussion during the meeting
- `BTW <comment>`
  - Comment syntax.  Runs until end of line.
