# Language Features

## Basic Syntax and Structure

### Program Lines
GW-BASIC programs consist of numbered lines executed in numerical order (unless control flow statements redirect execution).

```basic
10 REM This is a comment
20 PRINT "Hello, World!"
30 END
```

### Line Numbers
- Range: 0 to 65529
- Can be any integer within this range
- Lines execute in numerical order
- Common practice: Increment by 10 to allow insertion of new lines

### Immediate Mode
Commands can be executed immediately without line numbers:
```basic
PRINT "This executes immediately"
```

## Data Types and Variables

### Numeric Data Types

#### Integer (%)
- Range: -32,768 to 32,767
- 16-bit signed integers
- Fastest arithmetic operations
- Suffix: `%` (optional for integer variables)

```basic
A% = 100
COUNT% = -1000
```

#### Single-Precision Floating Point (!)
- Range: ±1.701412E-38 to ±3.402823E+38
- Approximately 7 decimal digits of precision
- Default numeric type
- Suffix: `!` (optional, default for numeric variables)

```basic
PI! = 3.141593
TEMPERATURE = 98.6
```

#### Double-Precision Floating Point (#)
- Range: ±4.940656E-324 to ±1.797693E+308
- Approximately 16 decimal digits of precision
- Suffix: `#` (required for double-precision variables)

```basic
PRECISE# = 3.141592653589793#
```

### String Data Type ($)
- Variable length (up to 255 characters)
- Suffix: `$` (required for string variables)
- Enclosed in double quotes in literals

```basic
NAME$ = "John Doe"
MESSAGE$ = "Welcome to GW-BASIC"
```

### Variable Names
- 1 to 40 characters long
- Must start with a letter (A-Z)
- Can contain letters, digits, and periods
- Case insensitive
- Type suffix determines data type

Valid examples:
```basic
A
NAME$
COUNTER%
AVERAGE
PI#
FIRST.NAME$
```

## Arrays

### Declaration
Arrays must be declared with the `DIM` statement before use:

```basic
DIM NUMBERS(100)        ' Single-precision array, 0 to 100
DIM NAMES$(50)          ' String array, 0 to 50
DIM MATRIX(10, 10)      ' Two-dimensional array
DIM TABLE%(5, 3, 2)     ' Three-dimensional integer array
```

### Indexing
- Arrays are zero-indexed by default
- Maximum 255 dimensions
- Each dimension can have up to 32,767 elements

```basic
DIM SCORES(9)           ' Elements 0 through 9
SCORES(0) = 85
SCORES(5) = 92
```

## Operators

### Arithmetic Operators
- `+` Addition
- `-` Subtraction  
- `*` Multiplication
- `/` Division (floating-point result)
- `\` Integer division (truncated result)
- `^` Exponentiation
- `MOD` Modulo (remainder)

```basic
A = 10 + 5              ' Result: 15
B = 10 / 3              ' Result: 3.333333
C = 10 \ 3              ' Result: 3
D = 2 ^ 3               ' Result: 8
E = 10 MOD 3            ' Result: 1
```

### Comparison Operators
- `=` Equal to
- `<>` Not equal to
- `<` Less than
- `>` Greater than
- `<=` Less than or equal to
- `>=` Greater than or equal to

### Logical Operators
- `AND` Logical AND
- `OR` Logical OR
- `NOT` Logical NOT
- `XOR` Exclusive OR
- `EQV` Equivalence
- `IMP` Implication

```basic
IF (A > 5) AND (B < 10) THEN PRINT "Condition met"
```

## Control Flow Statements

### Conditional Statements

#### IF...THEN...ELSE
```basic
IF condition THEN statement(s) [ELSE statement(s)]
```

Examples:
```basic
10 IF A > 5 THEN PRINT "Greater than 5"
20 IF B < 0 THEN PRINT "Negative" ELSE PRINT "Non-negative"
30 IF X = 0 THEN GOTO 100 ELSE Y = 1/X
```

#### Multi-line IF blocks:
```basic
10 IF SCORE >= 90 THEN
20   GRADE$ = "A"
30   PRINT "Excellent!"
40 ELSE
50   IF SCORE >= 80 THEN
60     GRADE$ = "B"
70   ELSE
80     GRADE$ = "C"
90   END IF
100 END IF
```

### Loop Statements

#### FOR...NEXT Loops
```basic
FOR variable = start TO end [STEP increment]
  [statements]
NEXT [variable]
```

Examples:
```basic
10 FOR I = 1 TO 10
20   PRINT I
30 NEXT I

40 FOR J = 10 TO 1 STEP -1
50   PRINT J;
60 NEXT
```

#### WHILE...WEND Loops
```basic
WHILE condition
  [statements]
WEND
```

Example:
```basic
10 I = 1
20 WHILE I <= 10
30   PRINT I
40   I = I + 1
50 WEND
```

### Branching Statements

#### GOTO
```basic
GOTO line_number
```

#### GOSUB...RETURN
```basic
10 GOSUB 1000
20 PRINT "Back from subroutine"
30 END
1000 PRINT "In subroutine"
1010 RETURN
```

#### ON...GOTO and ON...GOSUB
```basic
10 INPUT "Enter 1, 2, or 3: "; N
20 ON N GOTO 100, 200, 300
30 PRINT "Invalid choice"
40 END
100 PRINT "You chose 1": END
200 PRINT "You chose 2": END  
300 PRINT "You chose 3": END
```

## Functions

### Built-in Mathematical Functions

#### Trigonometric Functions
- `SIN(x)` - Sine (x in radians)
- `COS(x)` - Cosine (x in radians)
- `TAN(x)` - Tangent (x in radians)
- `ATN(x)` - Arctangent (result in radians)

#### Other Mathematical Functions
- `ABS(x)` - Absolute value
- `SGN(x)` - Sign (-1, 0, or 1)
- `SQR(x)` - Square root
- `INT(x)` - Integer part (truncate)
- `RND(x)` - Random number
- `EXP(x)` - e raised to power x
- `LOG(x)` - Natural logarithm

```basic
10 X = 3.14159 / 4
20 PRINT "SIN(45°) ="; SIN(X)
30 PRINT "Square root of 16 ="; SQR(16)
40 PRINT "Random number:"; RND(1)
```

### String Functions

#### String Manipulation
- `LEN(string$)` - Length of string
- `LEFT$(string$, n)` - Leftmost n characters
- `RIGHT$(string$, n)` - Rightmost n characters  
- `MID$(string$, start, length)` - Substring
- `CHR$(code)` - Character from ASCII code
- `ASC(string$)` - ASCII code of first character
- `STR$(number)` - Convert number to string
- `VAL(string$)` - Convert string to number

```basic
10 A$ = "HELLO WORLD"
20 PRINT LEN(A$)              ' Prints: 11
30 PRINT LEFT$(A$, 5)         ' Prints: HELLO
40 PRINT MID$(A$, 7, 5)       ' Prints: WORLD
50 PRINT ASC("A")             ' Prints: 65
60 PRINT CHR$(65)             ' Prints: A
```

#### String Operations
- `INSTR([start,] string1$, string2$)` - Find substring position
- `SPACE$(n)` - String of n spaces
- `STRING$(n, character)` - String of repeated characters

```basic
10 TEXT$ = "Programming in BASIC"
20 POS = INSTR(TEXT$, "BASIC")
30 PRINT "BASIC found at position"; POS
```

### Type Conversion Functions
- `CINT(x)` - Convert to integer
- `CSNG(x)` - Convert to single-precision
- `CDBL(x)` - Convert to double-precision

### User-Defined Functions
```basic
10 DEF FN AREA(R) = 3.14159 * R * R
20 INPUT "Radius: "; RADIUS
30 PRINT "Area ="; FN AREA(RADIUS)
```

## Input/Output

### Screen Output
- `PRINT` - Display text and numbers
- `PRINT USING` - Formatted output
- `?` - Shorthand for PRINT

```basic
10 PRINT "Hello, World!"
20 ? "This also prints"
30 PRINT "Value:", 42
40 PRINT 10; 20; 30          ' Semicolon for compact spacing
50 PRINT 10, 20, 30          ' Comma for tabular spacing
```

### Keyboard Input
- `INPUT` - Get user input
- `INPUT$` - Get specific number of characters
- `INKEY$` - Check for key press (non-blocking)

```basic
10 INPUT "Enter your name: "; NAME$
20 INPUT "Enter two numbers: "; A, B
30 PRINT "Sum ="; A + B
```

### Screen Control
- `CLS` - Clear screen
- `LOCATE row, column` - Position cursor
- `COLOR foreground, background` - Set colors
- `WIDTH columns` - Set screen width

## File Operations

### Sequential Files
```basic
10 OPEN "DATA.TXT" FOR OUTPUT AS #1
20 PRINT #1, "Hello, File!"
30 CLOSE #1
40 OPEN "DATA.TXT" FOR INPUT AS #1
50 INPUT #1, MESSAGE$
60 PRINT MESSAGE$
70 CLOSE #1
```

### Random Access Files
```basic
10 OPEN "RECORDS.DAT" FOR RANDOM AS #1 LEN = 50
20 FIELD #1, 30 AS NAME$, 20 AS ADDRESS$
30 LSET NAME$ = "John Doe"
40 LSET ADDRESS$ = "123 Main St"
50 PUT #1, 1
60 GET #1, 1
70 PRINT NAME$, ADDRESS$
80 CLOSE #1
```

## Error Handling

### Error Trapping
```basic
10 ON ERROR GOTO 1000
20 INPUT "Enter a number: "; N
30 PRINT "Result:", 100 / N
40 END
1000 PRINT "Error occurred: "; ERR
1010 RESUME NEXT
```

### Error Information
- `ERR` - Error code number
- `ERL` - Line number where error occurred
- `RESUME` - Continue after error
- `RESUME NEXT` - Continue at next statement
- `RESUME line_number` - Continue at specific line

## Comments and Documentation

### REM Statement
```basic
10 REM This is a comment
20 ' This is also a comment (shorthand)
```

### Multiple Statements per Line
Use colon (`:`) to separate statements:
```basic
10 A = 5: B = 10: PRINT A + B
```

## Memory and System Functions

### Memory Information
- `FRE(0)` - Available string space
- `FRE(1)` - Available numeric space

### System Functions
- `PEEK(address)` - Read memory byte
- `POKE address, value` - Write memory byte
- `USR(x)` - Call machine language routine
- `VARPTR(variable)` - Get variable address

This covers the core language features of GW-BASIC. The next sections will provide detailed command references and programming examples.
