# Variables and Data Types

## Variable Naming Conventions

### Basic Rules
- Variable names must start with a letter (A-Z, case insensitive)
- Can contain letters, digits (0-9), and periods (.)
- Maximum length: 40 characters
- Cannot use reserved words (like PRINT, FOR, etc.)
- Case insensitive: `Variable`, `VARIABLE`, and `variable` are the same

### Type Suffixes
Variables are distinguished by their type suffix:
- `%` - Integer
- `!` - Single-precision floating point (default, can be omitted)
- `#` - Double-precision floating point
- `$` - String

### Valid Examples
```basic
A               ' Single-precision (default)
COUNT%          ' Integer
PI#             ' Double-precision
NAME$           ' String
FIRST.NAME$     ' String with period
STUDENT.GRADE%  ' Integer with period
```

### Invalid Examples
```basic
123VAR          ' Cannot start with digit
FOR%            ' Cannot use reserved word
VERY-LONG-NAME  ' Hyphens not allowed
```

## Numeric Data Types

### Integer (%)
Integers are 16-bit signed values stored in two's complement format.

**Range**: -32,768 to 32,767
**Memory**: 2 bytes per variable
**Precision**: Exact for whole numbers within range

```basic
10 COUNT% = 1000
20 MAX% = 32767
30 MIN% = -32768
40 PRINT COUNT%, MAX%, MIN%
```

**Advantages**:
- Fastest arithmetic operations
- Exact representation
- Least memory usage

**Disadvantages**:
- Limited range
- No fractional parts
- Overflow errors if range exceeded

**Overflow Behavior**:
```basic
10 A% = 32767
20 A% = A% + 1          ' Causes "Overflow" error
```

### Single-Precision Floating Point (!)
Single-precision numbers use IEEE-like floating point format.

**Range**: ±1.701412E-38 to ±3.402823E+38
**Memory**: 4 bytes per variable
**Precision**: Approximately 7 decimal digits

```basic
10 PI! = 3.141593
20 TEMP = 98.6          ' ! suffix optional (default)
30 SMALL = 1.23E-15
40 LARGE = 9.87E+20
```

**Scientific Notation**:
```basic
10 A = 1.23E5           ' 123000
20 B = 4.56E-3          ' 0.00456
30 PRINT A, B
```

**Precision Limitations**:
```basic
10 A = 1234567.8        ' Stored as 1234568 (rounded)
20 B = 0.1 + 0.2        ' May not equal exactly 0.3
30 PRINT A, B
```

### Double-Precision Floating Point (#)
Double-precision provides extended range and precision.

**Range**: ±4.940656E-324 to ±1.797693E+308
**Memory**: 8 bytes per variable
**Precision**: Approximately 16 decimal digits

```basic
10 PRECISE# = 3.141592653589793#
20 HUGE# = 1.23456789012345D+100
30 TINY# = 9.87654321098765D-200
```

**When to Use Double-Precision**:
- Scientific calculations requiring high precision
- Financial calculations with many decimal places
- Accumulation of many small values
- Working with very large or very small numbers

## String Data Type ($)

### String Basics
Strings are sequences of characters enclosed in double quotes.

**Maximum Length**: 255 characters
**Memory**: Variable, stored in string space
**Suffix**: `$` (required)

```basic
10 NAME$ = "John Doe"
20 MESSAGE$ = "Hello, World!"
30 EMPTY$ = ""
40 LONG$ = STRING$(100, "*")    ' 100 asterisks
```

### String Literals
```basic
10 A$ = "Hello"                 ' Simple string
20 B$ = "Line 1" + CHR$(13) + CHR$(10) + "Line 2"  ' Multi-line
30 C$ = "He said, ""Hello"""    ' Embedded quotes
40 D$ = "Path: C:\BASIC\PROG"   ' Backslashes OK
```

### String Concatenation
Use the `+` operator to join strings:
```basic
10 FIRST$ = "John"
20 LAST$ = "Doe"
30 FULL$ = FIRST$ + " " + LAST$
40 PRINT FULL$                  ' Prints: John Doe
```

### String Memory Management
Strings use a garbage-collected heap:
```basic
10 FOR I = 1 TO 1000
20   TEMP$ = "Temporary string " + STR$(I)
30 NEXT I
' Garbage collection occurs automatically when string space fills
```

## Type Conversion

### Automatic Conversion
GW-BASIC performs automatic type conversion in mixed expressions:

```basic
10 A% = 5               ' Integer
20 B = 3.7              ' Single-precision
30 C# = 2.1#            ' Double-precision
40 RESULT = A% + B + C# ' All converted to double-precision
```

**Conversion Hierarchy** (lowest to highest precision):
1. Integer (%)
2. Single-precision (!)
3. Double-precision (#)

### Explicit Conversion Functions

#### Numeric Conversions
```basic
' To Integer
10 A% = CINT(3.7)       ' Result: 4 (rounded)
20 B% = CINT(-3.7)      ' Result: -4 (rounded)

' To Single-Precision
30 C! = CSNG(123#)      ' Convert double to single

' To Double-Precision
40 D# = CDBL(456%)      ' Convert integer to double
```

#### String to Numeric
```basic
10 A$ = "123.45"
20 NUM = VAL(A$)        ' Result: 123.45
30 B$ = "  -987  "
40 NEG = VAL(B$)        ' Result: -987 (ignores leading/trailing spaces)
50 C$ = "12.3ABC"
60 PARTIAL = VAL(C$)    ' Result: 12.3 (stops at first non-numeric)
```

#### Numeric to String
```basic
10 NUM = 123.45
20 STR1$ = STR$(NUM)    ' Result: " 123.45" (note leading space)
30 STR2$ = LTRIM$(STR$(NUM))  ' Remove leading space: "123.45"
```

### Rounding vs. Truncation
```basic
' CINT rounds to nearest integer
10 PRINT CINT(3.4)      ' Prints: 3
20 PRINT CINT(3.6)      ' Prints: 4
30 PRINT CINT(-3.4)     ' Prints: -3
40 PRINT CINT(-3.6)     ' Prints: -4

' INT truncates toward negative infinity
50 PRINT INT(3.7)       ' Prints: 3
60 PRINT INT(-3.7)      ' Prints: -4

' FIX truncates toward zero
70 PRINT FIX(3.7)       ' Prints: 3
80 PRINT FIX(-3.7)      ' Prints: -3
```

## Arrays

### Array Declaration
Arrays must be declared with `DIM` before use:

```basic
10 DIM NUMBERS(100)     ' Single-precision array, indices 0-100
20 DIM NAMES$(50)       ' String array, indices 0-50
30 DIM SCORES%(25)      ' Integer array, indices 0-25
40 DIM VALUES#(10)      ' Double-precision array, indices 0-10
```

### Multi-Dimensional Arrays
```basic
10 DIM MATRIX(10, 10)           ' 2D array: 11x11 elements
20 DIM TABLE%(5, 3, 2)          ' 3D array: 6x4x3 elements
30 DIM SPREADSHEET$(100, 26)    ' 2D string array: 101x27 elements
```

### Array Indexing
By default, arrays are zero-indexed:
```basic
10 DIM SCORES(9)        ' Elements: SCORES(0) through SCORES(9)
20 SCORES(0) = 85
30 SCORES(5) = 92
40 FOR I = 0 TO 9
50   PRINT "Score"; I; "="; SCORES(I)
60 NEXT I
```

### OPTION BASE
Change the default lower bound:
```basic
10 OPTION BASE 1        ' Arrays start at index 1
20 DIM GRADES(10)       ' Elements: GRADES(1) through GRADES(10)
```

### Explicit Bounds
Specify both lower and upper bounds:
```basic
10 DIM TEMPS(1980 TO 2020)      ' Years 1980-2020
20 DIM GRID(-10 TO 10, -10 TO 10)  ' Centered coordinate system
```

### Array Memory Usage
- Integer arrays: 2 bytes per element
- Single-precision arrays: 4 bytes per element  
- Double-precision arrays: 8 bytes per element
- String arrays: Variable (pointers + string data)

```basic
10 DIM BIG_ARRAY(1000)  ' Uses 4004 bytes (1001 elements × 4 bytes)
```

### Array Limitations
- Maximum 255 dimensions
- Each dimension can have up to 32,767 elements
- Total array size limited by available memory
- Arrays cannot be redimensioned (use ERASE to remove)

## Variable Storage and Memory

### Memory Organization
GW-BASIC organizes memory into several areas:

1. **Program Storage**: Tokenized program code
2. **Simple Variables**: Numeric and string variables
3. **Arrays**: Multi-dimensional arrays
4. **String Space**: Storage for string data
5. **Stack**: Subroutine calls and FOR loops

### Variable Storage Order
Variables are stored in the order they are first referenced:
```basic
10 ZEBRA = 1            ' Stored first
20 ALPHA = 2            ' Stored second
30 BETA = 3             ' Stored third
```

### String Space Management
```basic
10 PRINT FRE(0)         ' Available string space
20 A$ = STRING$(1000, "X")
30 PRINT FRE(0)         ' Less space available
40 A$ = ""              ' String data can be garbage collected
```

### Memory Conservation Tips
1. Use integers when possible (smallest storage)
2. Declare arrays with appropriate bounds
3. Release unused string variables: `VAR$ = ""`
4. Use `CLEAR` to reset all variables

## Variable Scope and Lifetime

### Global Variables
All variables in GW-BASIC are global by default:
```basic
10 A = 100
20 GOSUB 1000
30 PRINT A              ' Prints: 200 (modified in subroutine)
40 END
1000 A = 200            ' Modifies global variable A
1010 RETURN
```

### Local Parameters in DEF FN
Function parameters are local to the function:
```basic
10 A = 5
20 DEF FN TEST(A) = A * 2    ' Parameter A is local
30 PRINT FN TEST(10)         ' Prints: 20
40 PRINT A                   ' Prints: 5 (global A unchanged)
```

### Variable Initialization
- Numeric variables initialize to 0
- String variables initialize to empty string ("")
- Array elements initialize to 0 or ""

```basic
10 PRINT X              ' Prints: 0
20 PRINT Y$             ' Prints: (empty string)
30 DIM ARR(5)
40 PRINT ARR(3)         ' Prints: 0
```

## Constants and Literals

### Numeric Constants
```basic
10 A = 123              ' Integer constant
20 B = 123.45           ' Floating-point constant
30 C = 1.23E5           ' Scientific notation (123000)
40 D = &HFF             ' Hexadecimal (255)
50 E = &O377            ' Octal (255)
```

### String Constants
```basic
10 MSG$ = "Hello"       ' String literal
20 QUOTE$ = CHR$(34)    ' Double quote character
30 TAB$ = CHR$(9)       ' Tab character
40 CRLF$ = CHR$(13) + CHR$(10)  ' Carriage return + line feed
```

### Named Constants (Using Variables)
```basic
10 PI = 3.141592653589793#
20 E = 2.718281828459045#
30 GOLDEN.RATIO = 1.618033988749895#
```

## Variable Performance Considerations

### Access Speed (fastest to slowest)
1. Integer variables (%)
2. Single-precision variables (!)
3. Double-precision variables (#)
4. String variables ($)
5. Array elements

### Memory Efficiency
- Use appropriate data types for your needs
- Integer: Exact values within range, fastest
- Single-precision: Good balance of range and speed
- Double-precision: Maximum precision, slower
- Strings: Variable memory usage

### Best Practices
```basic
' Use integers for counters and flags
10 FOR COUNT% = 1 TO 1000
20   ' loop body
30 NEXT COUNT%

' Use single-precision for most calculations
40 AREA = LENGTH * WIDTH

' Use double-precision for high-precision work
50 RESULT# = SIN(ANGLE#) + COS(ANGLE#)

' Minimize string operations in tight loops
60 FOR I = 1 TO 100
70   ' Avoid: MSG$ = "Value: " + STR$(I)
80   ' Better: Do string operations outside loop
90 NEXT I
```

This comprehensive guide covers all aspects of variables and data types in GW-BASIC, providing the foundation for effective programming in the language.
