# Commands Reference

This section provides a comprehensive reference of all GW-BASIC commands, organized alphabetically for easy lookup.

## A

### ABS
**Function**: Returns the absolute value of a numeric expression.

**Syntax**: `ABS(numeric_expression)`

**Example**:
```basic
10 PRINT ABS(-5)        ' Prints: 5
20 PRINT ABS(3.14)      ' Prints: 3.14
30 X = -10: PRINT ABS(X) ' Prints: 10
```

### ASC
**Function**: Returns the ASCII code of the first character in a string.

**Syntax**: `ASC(string_expression)`

**Example**:
```basic
10 PRINT ASC("A")       ' Prints: 65
20 PRINT ASC("Hello")   ' Prints: 72 (ASCII of 'H')
30 CHAR$ = "Z": PRINT ASC(CHAR$) ' Prints: 90
```

### ATN
**Function**: Returns the arctangent of a numeric expression in radians.

**Syntax**: `ATN(numeric_expression)`

**Example**:
```basic
10 PRINT ATN(1)         ' Prints: 0.785398 (π/4)
20 ANGLE = ATN(1) * 4   ' Calculate π
30 PRINT "π ="; ANGLE   ' Prints: π = 3.141593
```

### AUTO
**Statement**: Automatically generates line numbers for program entry.

**Syntax**: `AUTO [start_line][,increment]`

**Parameters**:
- `start_line`: Starting line number (default: 10)
- `increment`: Increment between lines (default: 10)

**Example**:
```basic
AUTO 100,5    ' Start at line 100, increment by 5
AUTO          ' Start at line 10, increment by 10
```

## B

### BEEP
**Statement**: Produces a beep sound through the computer's speaker.

**Syntax**: `BEEP`

**Example**:
```basic
10 PRINT "Press any key..."
20 BEEP
30 A$ = INPUT$(1)
```

### BLOAD
**Statement**: Loads a binary file from disk into memory.

**Syntax**: `BLOAD filename[,offset]`

**Parameters**:
- `filename`: Name of binary file to load
- `offset`: Memory offset where file should be loaded

**Example**:
```basic
10 BLOAD "PICTURE.BIN", 16384
```

### BSAVE
**Statement**: Saves a portion of memory to a binary file.

**Syntax**: `BSAVE filename, offset, length`

**Parameters**:
- `filename`: Name of file to create
- `offset`: Starting memory address
- `length`: Number of bytes to save

**Example**:
```basic
10 BSAVE "SCREEN.BIN", 16384, 16384
```

## C

### CALL
**Statement**: Calls a machine language subroutine.

**Syntax**: `CALL variable[(parameter_list)]`

**Example**:
```basic
10 DEF SEG = &H2000
20 CALL ROUTINE(A%, B$, C#)
```

### CDBL
**Function**: Converts a numeric expression to double-precision.

**Syntax**: `CDBL(numeric_expression)`

**Example**:
```basic
10 A = 3.14159
20 B# = CDBL(A)
30 PRINT B#
```

### CHAIN
**Statement**: Loads and runs another BASIC program.

**Syntax**: `CHAIN filename[,line_number][,ALL][,DELETE range]`

**Example**:
```basic
10 CHAIN "MENU.BAS"
20 CHAIN "PART2.BAS", 1000, ALL
```

### CHR$
**Function**: Returns the character corresponding to an ASCII code.

**Syntax**: `CHR$(ascii_code)`

**Example**:
```basic
10 PRINT CHR$(65)       ' Prints: A
20 PRINT CHR$(13)       ' Prints carriage return
30 BEEP$ = CHR$(7): PRINT BEEP$  ' Sounds beep
```

### CINT
**Function**: Converts a numeric expression to integer.

**Syntax**: `CINT(numeric_expression)`

**Example**:
```basic
10 A = 3.7
20 B% = CINT(A)         ' B% = 4 (rounded)
30 PRINT B%
```

### CIRCLE
**Statement**: Draws a circle or arc.

**Syntax**: `CIRCLE (x,y), radius[, color][, start][, end][, aspect]`

**Example**:
```basic
10 SCREEN 1
20 CIRCLE (160, 100), 50
30 CIRCLE (100, 75), 25, 2, 0, 3.14159  ' Half circle
```

### CLEAR
**Statement**: Reinitializes variables and sets memory limits.

**Syntax**: `CLEAR [,string_space][,stack_space]`

**Example**:
```basic
10 CLEAR            ' Clear all variables
20 CLEAR , 1000     ' Reserve 1000 bytes for strings
30 CLEAR , , 512    ' Set stack space to 512 bytes
```

### CLOSE
**Statement**: Closes one or more files.

**Syntax**: `CLOSE [[#]file_number[,[#]file_number]...]`

**Example**:
```basic
10 CLOSE #1         ' Close file #1
20 CLOSE            ' Close all open files
30 CLOSE #1, #2, #3 ' Close multiple files
```

### CLS
**Statement**: Clears the screen and homes the cursor.

**Syntax**: `CLS [color_value]`

**Example**:
```basic
10 CLS              ' Clear screen
20 CLS 1            ' Clear screen with blue background
```

### COLOR
**Statement**: Sets foreground, background, and border colors.

**Syntax**: `COLOR [foreground][,background][,border]`

**Example**:
```basic
10 COLOR 15, 1      ' White on blue
20 COLOR , 0        ' Change background to black
30 COLOR 14         ' Change foreground to yellow
```

### COM
**Statement**: Enables or disables communication port interrupts.

**Syntax**: `COM(n) ON/OFF/STOP`

**Example**:
```basic
10 COM(1) ON
20 ON COM(1) GOSUB 1000
```

### COMMON
**Statement**: Defines variables to pass between chained programs.

**Syntax**: `COMMON variable_list`

**Example**:
```basic
10 COMMON A, B$, ARRAY()
20 A = 100: B$ = "Data"
30 CHAIN "NEXT.BAS"
```

### CONT
**Statement**: Continues program execution after STOP or Ctrl+Break.

**Syntax**: `CONT`

**Example**:
```basic
10 FOR I = 1 TO 100
20   PRINT I
30   IF I = 50 THEN STOP
40 NEXT I
```
After STOP: `CONT` resumes at line 40.

### COS
**Function**: Returns the cosine of an angle in radians.

**Syntax**: `COS(numeric_expression)`

**Example**:
```basic
10 PRINT COS(0)         ' Prints: 1
20 PRINT COS(3.14159)   ' Prints: -1
30 ANGLE = 60 * 3.14159/180  ' 60 degrees in radians
40 PRINT COS(ANGLE)     ' Prints: 0.5
```

### CSNG
**Function**: Converts a numeric expression to single-precision.

**Syntax**: `CSNG(numeric_expression)`

**Example**:
```basic
10 A# = 3.141592653589793#
20 B! = CSNG(A#)
30 PRINT B!            ' Prints: 3.141593
```

### CSRLIN
**Function**: Returns the current cursor row position.

**Syntax**: `CSRLIN`

**Example**:
```basic
10 PRINT "Current row:"; CSRLIN
20 LOCATE 10, 20
30 PRINT "Now at row:"; CSRLIN
```

### CVD, CVI, CVS
**Functions**: Convert string to numeric value.

**Syntax**: 
- `CVD(string_expression)` - Convert to double-precision
- `CVI(string_expression)` - Convert to integer  
- `CVS(string_expression)` - Convert to single-precision

**Example**:
```basic
10 A$ = MKD$(123.456#)
20 PRINT CVD(A$)        ' Prints: 123.456
```

## D

### DATA
**Statement**: Stores numeric and string constants for READ statements.

**Syntax**: `DATA constant[,constant]...`

**Example**:
```basic
10 DATA 10, 20, "Hello", 3.14159
20 READ A, B, C$, D
30 PRINT A, B, C$, D
```

### DATE$
**Function/Statement**: Gets or sets the system date.

**Syntax**: 
- `DATE$` (function) - Returns current date
- `DATE$ = date_string` (statement) - Sets date

**Example**:
```basic
10 PRINT "Today is "; DATE$
20 DATE$ = "12-25-1983"
```

### DEF FN
**Statement**: Defines a user function.

**Syntax**: `DEF FN name[(parameter_list)] = expression`

**Example**:
```basic
10 DEF FN SQUARE(X) = X * X
20 DEF FN MAX(A, B) = (A + B + ABS(A - B)) / 2
30 PRINT FN SQUARE(5)      ' Prints: 25
40 PRINT FN MAX(10, 7)     ' Prints: 10
```

### DEFDBL, DEFINT, DEFSNG, DEFSTR
**Statements**: Set default data types for variables.

**Syntax**: 
- `DEFDBL letter_range`
- `DEFINT letter_range`
- `DEFSNG letter_range`
- `DEFSTR letter_range`

**Example**:
```basic
10 DEFINT A-F          ' Variables A-F are integers
20 DEFDBL G-M          ' Variables G-M are double-precision
30 DEFSTR N-Z          ' Variables N-Z are strings
```

### DELETE
**Statement**: Deletes program lines.

**Syntax**: `DELETE line_number[-line_number]`

**Example**:
```basic
DELETE 100         ' Delete line 100
DELETE 200-300     ' Delete lines 200 through 300
DELETE -50         ' Delete lines up to 50
DELETE 1000-       ' Delete lines from 1000 to end
```

### DIM
**Statement**: Declares arrays and allocates memory.

**Syntax**: `DIM variable(subscripts)[,variable(subscripts)]...`

**Example**:
```basic
10 DIM A(100)              ' Single dimension
20 DIM B$(50), C%(25)      ' Multiple arrays
30 DIM MATRIX(10, 10)      ' Two dimensions
40 DIM TABLE(5, 3, 2)      ' Three dimensions
```

### DRAW
**Statement**: Draws lines and shapes using a graphics macro language.

**Syntax**: `DRAW string_expression`

**Example**:
```basic
10 SCREEN 1
20 DRAW "M160,100"         ' Move to center
30 DRAW "U50 R50 D50 L50"  ' Draw square
40 DRAW "BM100,100 C2 M+50,+50"  ' Move and change color
```

## E

### EDIT
**Statement**: Invokes the line editor for a program line.

**Syntax**: `EDIT line_number`

**Example**:
```basic
EDIT 100      ' Edit line 100
```

### ELSE
**Statement**: Provides alternative execution in IF statements.

**Syntax**: `IF condition THEN statements ELSE statements`

**Example**:
```basic
10 IF X > 0 THEN PRINT "Positive" ELSE PRINT "Zero or negative"
```

### END
**Statement**: Terminates program execution.

**Syntax**: `END`

**Example**:
```basic
10 PRINT "Program finished"
20 END
30 PRINT "This won't execute"
```

### ENVIRON
**Statement**: Sets environment variable.

**Syntax**: `ENVIRON string_expression`

**Example**:
```basic
10 ENVIRON "PATH=C:\DOS;C:\BASIC"
```

### EOF
**Function**: Tests for end of file.

**Syntax**: `EOF(file_number)`

**Example**:
```basic
10 OPEN "DATA.TXT" FOR INPUT AS #1
20 WHILE NOT EOF(1)
30   INPUT #1, A$
40   PRINT A$
50 WEND
60 CLOSE #1
```

### EQV
**Operator**: Logical equivalence operator.

**Syntax**: `expression1 EQV expression2`

**Example**:
```basic
10 A = 5: B = 5
20 IF (A > 3) EQV (B > 3) THEN PRINT "Both true or both false"
```

### ERASE
**Statement**: Removes arrays from memory.

**Syntax**: `ERASE array_name[,array_name]...`

**Example**:
```basic
10 DIM A(100), B$(50)
20 ERASE A, B$
```

### ERL
**Function**: Returns line number where last error occurred.

**Syntax**: `ERL`

**Example**:
```basic
10 ON ERROR GOTO 1000
20 ' ... program code ...
1000 PRINT "Error at line"; ERL
```

### ERR
**Function**: Returns error code of last error.

**Syntax**: `ERR`

**Example**:
```basic
1000 IF ERR = 53 THEN PRINT "File not found"
1010 IF ERR = 61 THEN PRINT "Disk full"
```

### ERROR
**Statement**: Simulates an error condition.

**Syntax**: `ERROR error_code`

**Example**:
```basic
10 INPUT "Enter error code: "; E
20 ERROR E
```

### EXP
**Function**: Returns e raised to a power.

**Syntax**: `EXP(numeric_expression)`

**Example**:
```basic
10 PRINT EXP(1)         ' Prints: 2.718282 (e)
20 PRINT EXP(0)         ' Prints: 1
```

## F

### FIELD
**Statement**: Allocates space for variables in random file buffer.

**Syntax**: `FIELD [#]file_number, width AS string_variable[,width AS string_variable]...`

**Example**:
```basic
10 OPEN "RECORDS.DAT" FOR RANDOM AS #1 LEN = 64
20 FIELD #1, 20 AS NAME$, 30 AS ADDRESS$, 14 AS PHONE$
```

### FILES
**Statement**: Displays directory of files.

**Syntax**: `FILES [filespec]`

**Example**:
```basic
10 FILES              ' List all files
20 FILES "*.BAS"      ' List BASIC files
30 FILES "A:"         ' List files on drive A
```

### FIX
**Function**: Truncates a number to an integer.

**Syntax**: `FIX(numeric_expression)`

**Example**:
```basic
10 PRINT FIX(3.7)       ' Prints: 3
20 PRINT FIX(-3.7)      ' Prints: -3
30 PRINT INT(-3.7)      ' Prints: -4 (difference from INT)
```

### FOR...NEXT
**Statement**: Creates a counting loop.

**Syntax**: 
```
FOR variable = start TO end [STEP increment]
  [statements]
NEXT [variable]
```

**Example**:
```basic
10 FOR I = 1 TO 10
20   PRINT I
30 NEXT I

40 FOR J = 10 TO 1 STEP -1
50   PRINT J;
60 NEXT
```

### FRE
**Function**: Returns amount of free memory.

**Syntax**: `FRE(numeric_expression)`

**Parameters**:
- `FRE(0)` or `FRE("")` - String space available
- `FRE(-1)` - Total free memory
- `FRE(-2)` - Stack space available

**Example**:
```basic
10 PRINT "String space:"; FRE(0)
20 PRINT "Total memory:"; FRE(-1)
```

## G

### GET
**Statement**: Reads data from random access file or gets graphics coordinates.

**Syntax**: 
- `GET [#]file_number[,record_number]`
- `GET (x1,y1)-(x2,y2), array_name`

**Example**:
```basic
10 OPEN "DATA.RND" FOR RANDOM AS #1 LEN = 64
20 GET #1, 5           ' Read record 5
30 CLOSE #1
```

### GOSUB...RETURN
**Statement**: Calls and returns from subroutine.

**Syntax**: 
- `GOSUB line_number`
- `RETURN`

**Example**:
```basic
10 GOSUB 1000
20 PRINT "Returned from subroutine"
30 END
1000 PRINT "In subroutine"
1010 RETURN
```

### GOTO
**Statement**: Unconditional branch to line number.

**Syntax**: `GOTO line_number`

**Example**:
```basic
10 PRINT "Start"
20 GOTO 100
30 PRINT "This is skipped"
100 PRINT "Jumped here"
```

## H

### HEX$
**Function**: Returns hexadecimal representation of number.

**Syntax**: `HEX$(numeric_expression)`

**Example**:
```basic
10 PRINT HEX$(255)      ' Prints: FF
20 PRINT HEX$(16)       ' Prints: 10
30 PRINT HEX$(0)        ' Prints: 0
```

## I

### IF...THEN...ELSE
**Statement**: Conditional execution.

**Syntax**: `IF condition THEN statement(s) [ELSE statement(s)]`

**Example**:
```basic
10 IF A > B THEN PRINT "A is greater"
20 IF X = 0 THEN PRINT "Zero" ELSE PRINT "Non-zero"
30 IF Y < 0 THEN Y = 0: PRINT "Corrected negative value"
```

### IMP
**Operator**: Logical implication operator.

**Syntax**: `expression1 IMP expression2`

**Example**:
```basic
10 A = -1: B = -1      ' True values
20 PRINT A IMP B       ' Prints: -1 (true)
```

### INKEY$
**Function**: Returns character from keyboard without waiting.

**Syntax**: `INKEY$`

**Example**:
```basic
10 PRINT "Press any key or ESC to quit"
20 K$ = INKEY$
30 IF K$ = "" THEN 20  ' No key pressed
40 IF K$ = CHR$(27) THEN END  ' ESC key
50 PRINT "You pressed: "; K$
```

### INP
**Function**: Returns byte from input port.

**Syntax**: `INP(port_number)`

**Example**:
```basic
10 STATUS = INP(64)    ' Read keyboard status
```

### INPUT
**Statement**: Gets input from keyboard or file.

**Syntax**: 
- `INPUT [;]["prompt";] variable_list`
- `INPUT #file_number, variable_list`

**Example**:
```basic
10 INPUT "Enter your name: "; NAME$
20 INPUT "Age, Height: "; AGE, HEIGHT
30 INPUT #1, A, B$     ' From file
```

### INPUT$
**Function**: Returns specified number of characters from keyboard or file.

**Syntax**: 
- `INPUT$(n)`
- `INPUT$(n, [#]file_number)`

**Example**:
```basic
10 PRINT "Press any key..."
20 A$ = INPUT$(1)      ' Wait for one character
30 PRINT "You pressed: "; A$
```

### INSTR
**Function**: Searches for substring within string.

**Syntax**: `INSTR([start,] string1$, string2$)`

**Example**:
```basic
10 TEXT$ = "Hello World"
20 POS = INSTR(TEXT$, "World")
30 PRINT "Found at position:"; POS    ' Prints: 7
40 POS = INSTR(5, TEXT$, "o")
50 PRINT "Second 'o' at:"; POS        ' Prints: 8
```

### INT
**Function**: Returns largest integer less than or equal to argument.

**Syntax**: `INT(numeric_expression)`

**Example**:
```basic
10 PRINT INT(3.7)       ' Prints: 3
20 PRINT INT(-3.7)      ' Prints: -4
30 PRINT INT(5)         ' Prints: 5
```

## K

### KEY
**Statement**: Defines function key strings or enables/disables function keys.

**Syntax**: 
- `KEY n, string_expression`
- `KEY ON/OFF/LIST`

**Example**:
```basic
10 KEY 1, "RUN" + CHR$(13)
20 KEY 2, "LIST" + CHR$(13)
30 KEY ON              ' Display function key line
```

### KILL
**Statement**: Deletes a file from disk.

**Syntax**: `KILL filespec`

**Example**:
```basic
10 KILL "OLDFILE.DAT"
20 KILL "TEMP.*"       ' Delete all TEMP files
```

## L

### LEFT$
**Function**: Returns leftmost characters from string.

**Syntax**: `LEFT$(string_expression, n)`

**Example**:
```basic
10 A$ = "Programming"
20 PRINT LEFT$(A$, 7)   ' Prints: Program
```

### LEN
**Function**: Returns length of string.

**Syntax**: `LEN(string_expression)`

**Example**:
```basic
10 NAME$ = "John Smith"
20 PRINT LEN(NAME$)     ' Prints: 10
```

### LET
**Statement**: Assigns value to variable (optional keyword).

**Syntax**: `[LET] variable = expression`

**Example**:
```basic
10 LET A = 5           ' Explicit LET
20 B = 10              ' Implicit assignment
```

### LINE
**Statement**: Draws lines and rectangles.

**Syntax**: `LINE [(x1,y1)]-(x2,y2)[,color][,B[F]]`

**Example**:
```basic
10 SCREEN 1
20 LINE (0,0)-(100,100), 2     ' Draw line
30 LINE (50,50)-(150,100), 3, B ' Draw box
40 LINE (10,10)-(90,90), 1, BF  ' Filled box
```

### LIST
**Statement**: Displays program lines.

**Syntax**: `LIST [line_number[-line_number]]`

**Example**:
```basic
LIST              ' List entire program
LIST 100          ' List line 100
LIST 100-200      ' List lines 100-200
LIST -50          ' List lines up to 50
LIST 1000-        ' List from line 1000 to end
```

### LLIST
**Statement**: Lists program to printer.

**Syntax**: `LLIST [line_number[-line_number]]`

**Example**:
```basic
LLIST             ' Print entire program
LLIST 100-200     ' Print lines 100-200
```

### LOAD
**Statement**: Loads a program from disk.

**Syntax**: `LOAD filename[,R]`

**Example**:
```basic
LOAD "MYPROG.BAS"     ' Load program
LOAD "PROG.BAS", R    ' Load and run
```

### LOC
**Function**: Returns current position in file.

**Syntax**: `LOC(file_number)`

**Example**:
```basic
10 OPEN "DATA.TXT" FOR INPUT AS #1
20 PRINT "Position:"; LOC(1)
```

### LOCATE
**Statement**: Positions cursor on screen.

**Syntax**: `LOCATE [row][,column][,cursor][,start][,stop]`

**Example**:
```basic
10 LOCATE 10, 20       ' Row 10, column 20
20 LOCATE , 1          ' Column 1, same row
30 LOCATE 1, 1, 1      ' Row 1, col 1, cursor on
```

### LOF
**Function**: Returns length of file in bytes.

**Syntax**: `LOF(file_number)`

**Example**:
```basic
10 OPEN "DATA.TXT" FOR INPUT AS #1
20 PRINT "File size:"; LOF(1); "bytes"
```

### LOG
**Function**: Returns natural logarithm.

**Syntax**: `LOG(numeric_expression)`

**Example**:
```basic
10 PRINT LOG(2.718282)  ' Prints: 1 (approximately)
20 PRINT LOG(10)        ' Prints: 2.302585
```

### LPOS
**Function**: Returns current print head position.

**Syntax**: `LPOS(printer_number)`

**Example**:
```basic
10 LPRINT "Hello";
20 PRINT "Print head at:"; LPOS(0)
```

### LPRINT
**Statement**: Prints to line printer.

**Syntax**: `LPRINT [expression_list][;]`

**Example**:
```basic
10 LPRINT "Printed output"
20 LPRINT A, B, C
30 LPRINT "No linefeed";
```

### LSET
**Statement**: Left-justifies string in field.

**Syntax**: `LSET string_variable = string_expression`

**Example**:
```basic
10 FIELD #1, 20 AS NAME$
20 LSET NAME$ = "John"  ' Left-justified in 20-char field
```

## M

### MERGE
**Statement**: Merges lines from disk file into current program.

**Syntax**: `MERGE filename`

**Example**:
```basic
MERGE "SUBROUT.BAS"    ' Merge subroutines
```

### MID$
**Function/Statement**: Returns or replaces substring.

**Syntax**: 
- `MID$(string, start[, length])` (function)
- `MID$(string_variable, start[, length]) = string_expression` (statement)

**Example**:
```basic
10 A$ = "Programming"
20 PRINT MID$(A$, 5, 4)    ' Prints: gram
30 MID$(A$, 1, 4) = "Code"
40 PRINT A$                ' Prints: Coderamming
```

### MKD$, MKI$, MKS$
**Functions**: Convert numeric values to string format for file storage.

**Syntax**: 
- `MKD$(double_precision_expression)`
- `MKI$(integer_expression)`
- `MKS$(single_precision_expression)`

**Example**:
```basic
10 A$ = MKI$(1000)
20 PUT #1, 1
```

### MOD
**Operator**: Modulo (remainder) operator.

**Syntax**: `expression1 MOD expression2`

**Example**:
```basic
10 PRINT 10 MOD 3       ' Prints: 1
20 PRINT 15 MOD 4       ' Prints: 3
```

### MOTOR
**Statement**: Controls cassette motor (if applicable).

**Syntax**: `MOTOR [ON/OFF]`

**Example**:
```basic
10 MOTOR ON
20 ' Cassette operations
30 MOTOR OFF
```

## N

### NAME
**Statement**: Renames a file.

**Syntax**: `NAME old_filename AS new_filename`

**Example**:
```basic
10 NAME "OLDNAME.TXT" AS "NEWNAME.TXT"
```

### NEW
**Statement**: Deletes current program from memory.

**Syntax**: `NEW`

**Example**:
```basic
NEW     ' Clear program and start fresh
```

### NEXT
**Statement**: End of FOR loop.

**Syntax**: `NEXT [variable[,variable]...]`

**Example**:
```basic
10 FOR I = 1 TO 10
20   FOR J = 1 TO 5
30     PRINT I * J
40   NEXT J
50 NEXT I
```

### NOT
**Operator**: Logical NOT operator.

**Syntax**: `NOT expression`

**Example**:
```basic
10 A = 0
20 IF NOT A THEN PRINT "A is false (zero)"
```

## O

### OCT$
**Function**: Returns octal representation of number.

**Syntax**: `OCT$(numeric_expression)`

**Example**:
```basic
10 PRINT OCT$(8)        ' Prints: 10
20 PRINT OCT$(64)       ' Prints: 100
```

### ON ERROR
**Statement**: Enables error trapping.

**Syntax**: `ON ERROR GOTO line_number`

**Example**:
```basic
10 ON ERROR GOTO 1000
20 ' Protected code here
1000 PRINT "Error:"; ERR; "at line"; ERL
1010 RESUME NEXT
```

### ON...GOSUB
**Statement**: Branch to subroutine based on expression value.

**Syntax**: `ON expression GOSUB line_number[,line_number]...`

**Example**:
```basic
10 INPUT "Enter 1, 2, or 3: "; N
20 ON N GOSUB 100, 200, 300
30 END
100 PRINT "Subroutine 1": RETURN
200 PRINT "Subroutine 2": RETURN
300 PRINT "Subroutine 3": RETURN
```

### ON...GOTO
**Statement**: Branch based on expression value.

**Syntax**: `ON expression GOTO line_number[,line_number]...`

**Example**:
```basic
10 INPUT "Enter 1, 2, or 3: "; N
20 ON N GOTO 100, 200, 300
100 PRINT "Choice 1": END
200 PRINT "Choice 2": END
300 PRINT "Choice 3": END
```

### OPEN
**Statement**: Opens file for input, output, or random access.

**Syntax**: `OPEN filename [FOR mode] AS [#]file_number [LEN=record_length]`

**Modes**: INPUT, OUTPUT, APPEND, RANDOM

**Example**:
```basic
10 OPEN "DATA.TXT" FOR INPUT AS #1
20 OPEN "OUTPUT.TXT" FOR OUTPUT AS #2
30 OPEN "RANDOM.DAT" FOR RANDOM AS #3 LEN = 128
```

### OPTION BASE
**Statement**: Sets default lower bound for arrays.

**Syntax**: `OPTION BASE n`

**Example**:
```basic
10 OPTION BASE 1       ' Arrays start at index 1
20 DIM A(10)           ' Elements 1 through 10
```

### OR
**Operator**: Logical OR operator.

**Syntax**: `expression1 OR expression2`

**Example**:
```basic
10 IF (A = 1) OR (B = 2) THEN PRINT "Condition met"
```

### OUT
**Statement**: Sends byte to output port.

**Syntax**: `OUT port_number, value`

**Example**:
```basic
10 OUT 888, 65         ' Send 'A' to port 888
```

## P

### PAINT
**Statement**: Fills an area with color or pattern.

**Syntax**: `PAINT (x,y)[,color][,border_color]`

**Example**:
```basic
10 SCREEN 1
20 CIRCLE (160, 100), 50
30 PAINT (160, 100), 2  ' Fill circle with color 2
```

### PEEK
**Function**: Returns byte value from memory address.

**Syntax**: `PEEK(address)`

**Example**:
```basic
10 VALUE = PEEK(1024)   ' Read memory location 1024
```

### PEN
**Function**: Returns light pen information.

**Syntax**: `PEN(n)`

**Example**:
```basic
10 X = PEN(3)          ' Get light pen X coordinate
20 Y = PEN(4)          ' Get light pen Y coordinate
```

### PLAY
**Statement**: Plays music using macro language.

**Syntax**: `PLAY string_expression`

**Example**:
```basic
10 PLAY "CDEFGAB"      ' Play scale
20 PLAY "T120 L4 CDEFGAB"  ' Tempo 120, quarter notes
```

### PMAP
**Function**: Maps coordinates between viewport and screen.

**Syntax**: `PMAP(coordinate, function)`

**Example**:
```basic
10 X = PMAP(50, 0)     ' Map viewport X to screen
20 Y = PMAP(100, 1)    ' Map viewport Y to screen
```

### POINT
**Function**: Returns color attribute of screen pixel.

**Syntax**: `POINT(x,y)`

**Example**:
```basic
10 SCREEN 1
20 PSET (100, 50), 2
30 COLOR_VAL = POINT(100, 50)
40 PRINT "Color at (100,50):"; COLOR_VAL
```

### POKE
**Statement**: Writes byte value to memory address.

**Syntax**: `POKE address, value`

**Example**:
```basic
10 POKE 1024, 65       ' Write 'A' to memory location 1024
```

### POS
**Function**: Returns current cursor column position.

**Syntax**: `POS(dummy_argument)`

**Example**:
```basic
10 PRINT "Hello";
20 PRINT "Column position:"; POS(0)
```

### PRESET
**Statement**: Resets (turns off) a graphics point.

**Syntax**: `PRESET (x,y)[,color]`

**Example**:
```basic
10 SCREEN 1
20 PRESET (100, 50)    ' Turn off pixel
30 PRESET (150, 75), 0 ' Set to background color
```

### PRINT
**Statement**: Displays output on screen.

**Syntax**: `PRINT [expression_list][;|,]`

**Example**:
```basic
10 PRINT "Hello World"
20 PRINT A, B, C       ' Tabular format
30 PRINT A; B; C       ' Compact format
40 PRINT A$;           ' No line feed
```

### PRINT USING
**Statement**: Displays formatted output.

**Syntax**: `PRINT USING format_string; expression_list`

**Example**:
```basic
10 PRINT USING "##.##"; 3.14159   ' Prints: 3.14
20 PRINT USING "###,###"; 12345   ' Prints: 12,345
30 PRINT USING "\    \"; "Hi"     ' Prints: Hi   
```

### PSET
**Statement**: Sets (turns on) a graphics point.

**Syntax**: `PSET (x,y)[,color]`

**Example**:
```basic
10 SCREEN 1
20 PSET (100, 50), 2   ' Set pixel to color 2
```

### PUT
**Statement**: Writes data to random access file or puts graphics.

**Syntax**: 
- `PUT [#]file_number[,record_number]`
- `PUT (x,y), array_name[,action_verb]`

**Example**:
```basic
10 OPEN "DATA.RND" FOR RANDOM AS #1 LEN = 64
20 PUT #1, 5           ' Write record 5
```

## Q

### (No commands begin with Q in GW-BASIC)

## R

### RANDOMIZE
**Statement**: Initializes random number generator.

**Syntax**: `RANDOMIZE [seed]`

**Example**:
```basic
10 RANDOMIZE           ' Use timer as seed
20 RANDOMIZE 12345     ' Use specific seed
30 PRINT RND(1)        ' Generate random number
```

### READ
**Statement**: Reads values from DATA statements.

**Syntax**: `READ variable_list`

**Example**:
```basic
10 DATA 10, 20, "Hello", 3.14
20 READ A, B, C$, D
30 PRINT A, B, C$, D
```

### REM
**Statement**: Indicates a comment (remark).

**Syntax**: `REM [comment]`

**Example**:
```basic
10 REM This is a comment
20 ' This is also a comment
```

### RENUM
**Statement**: Renumbers program lines.

**Syntax**: `RENUM [new_start][,old_start][,increment]`

**Example**:
```basic
RENUM              ' Start at 10, increment by 10
RENUM 100          ' Start at 100, increment by 10
RENUM 1000, 500, 5 ' Start at 1000, from line 500, step 5
```

### RESET
**Statement**: Closes all files.

**Syntax**: `RESET`

**Example**:
```basic
10 RESET           ' Close all open files
```

### RESTORE
**Statement**: Allows DATA statements to be reread.

**Syntax**: `RESTORE [line_number]`

**Example**:
```basic
10 DATA 1, 2, 3
20 READ A: PRINT A     ' Prints: 1
30 RESTORE
40 READ B: PRINT B     ' Prints: 1 (reread)
```

### RESUME
**Statement**: Continues execution after error.

**Syntax**: 
- `RESUME`
- `RESUME NEXT`
- `RESUME line_number`

**Example**:
```basic
1000 ON ERROR GOTO 2000
1010 ' ... code that might cause error ...
2000 PRINT "Error handled"
2010 RESUME NEXT       ' Continue at next statement
```

### RETURN
**Statement**: Returns from subroutine.

**Syntax**: `RETURN [line_number]`

**Example**:
```basic
10 GOSUB 1000
20 END
1000 PRINT "In subroutine"
1010 RETURN
```

### RIGHT$
**Function**: Returns rightmost characters from string.

**Syntax**: `RIGHT$(string_expression, n)`

**Example**:
```basic
10 A$ = "Programming"
20 PRINT RIGHT$(A$, 7)  ' Prints: gramming
```

### RND
**Function**: Returns random number.

**Syntax**: `RND[(n)]`

**Parameters**:
- `RND(1)` or `RND` - Random number 0 to 1
- `RND(0)` - Repeat last random number
- `RND(negative)` - Seed generator

**Example**:
```basic
10 RANDOMIZE
20 PRINT RND(1)        ' Random 0 to 1
30 DICE = INT(RND(1) * 6) + 1  ' Random 1 to 6
```

### RSET
**Statement**: Right-justifies string in field.

**Syntax**: `RSET string_variable = string_expression`

**Example**:
```basic
10 FIELD #1, 20 AS NAME$
20 RSET NAME$ = "John"  ' Right-justified in 20-char field
```

### RUN
**Statement**: Executes current program.

**Syntax**: `RUN [line_number]`

**Example**:
```basic
RUN            ' Run from beginning
RUN 1000       ' Start at line 1000
```

## S

### SAVE
**Statement**: Saves current program to disk.

**Syntax**: `SAVE filename[,A|P]`

**Parameters**:
- `A` - Save as ASCII text
- `P` - Save with protection

**Example**:
```basic
SAVE "MYPROG.BAS"      ' Save in tokenized format
SAVE "MYPROG.BAS", A   ' Save as ASCII text
```

### SCREEN
**Statement/Function**: Sets screen mode or returns character/color.

**Syntax**: 
- `SCREEN mode[,color_switch][,active_page][,visual_page]`
- `SCREEN(row, column[, color_flag])`

**Example**:
```basic
10 SCREEN 0            ' Text mode
20 SCREEN 1            ' Graphics mode
30 CHAR = SCREEN(10, 20)  ' Get character at row 10, col 20
```

### SGN
**Function**: Returns sign of numeric expression.

**Syntax**: `SGN(numeric_expression)`

**Returns**: -1 (negative), 0 (zero), 1 (positive)

**Example**:
```basic
10 PRINT SGN(-5)       ' Prints: -1
20 PRINT SGN(0)        ' Prints: 0
30 PRINT SGN(10)       ' Prints: 1
```

### SHELL
**Statement**: Executes DOS command.

**Syntax**: `SHELL [command_string]`

**Example**:
```basic
10 SHELL "DIR"         ' Execute DIR command
20 SHELL               ' Go to DOS prompt (EXIT to return)
```

### SIN
**Function**: Returns sine of angle in radians.

**Syntax**: `SIN(numeric_expression)`

**Example**:
```basic
10 PRINT SIN(0)        ' Prints: 0
20 ANGLE = 3.14159 / 2 ' 90 degrees
30 PRINT SIN(ANGLE)    ' Prints: 1
```

### SOUND
**Statement**: Generates sound through speaker.

**Syntax**: `SOUND frequency, duration`

**Example**:
```basic
10 SOUND 440, 18.2     ' A note for 1 second
20 SOUND 880, 9.1      ' Higher A for 0.5 seconds
```

### SPACE$
**Function**: Returns string of spaces.

**Syntax**: `SPACE$(n)`

**Example**:
```basic
10 PRINT "Hello" + SPACE$(5) + "World"
20 INDENT$ = SPACE$(10)
```

### SPC
**Function**: Skips spaces in PRINT statement.

**Syntax**: `SPC(n)`

**Example**:
```basic
10 PRINT "Hello"; SPC(10); "World"
```

### SQR
**Function**: Returns square root.

**Syntax**: `SQR(numeric_expression)`

**Example**:
```basic
10 PRINT SQR(16)       ' Prints: 4
20 PRINT SQR(2)        ' Prints: 1.414214
```

### STEP
**Keyword**: Specifies increment in FOR loops.

**Syntax**: `FOR variable = start TO end STEP increment`

**Example**:
```basic
10 FOR I = 1 TO 10 STEP 2    ' 1, 3, 5, 7, 9
20   PRINT I
30 NEXT I
```

### STICK
**Function**: Returns joystick coordinate.

**Syntax**: `STICK(n)`

**Example**:
```basic
10 X = STICK(0)        ' Get X coordinate
20 Y = STICK(1)        ' Get Y coordinate
```

### STOP
**Statement**: Halts program execution.

**Syntax**: `STOP`

**Example**:
```basic
10 FOR I = 1 TO 100
20   PRINT I
30   IF I = 50 THEN STOP
40 NEXT I
```

### STR$
**Function**: Converts number to string.

**Syntax**: `STR$(numeric_expression)`

**Example**:
```basic
10 A = 123
20 A$ = STR$(A)
30 PRINT "Number: " + A$    ' Prints: Number:  123
```

### STRING$
**Function**: Returns string of repeated characters.

**Syntax**: `STRING$(length, character)`

**Example**:
```basic
10 PRINT STRING$(10, "*")   ' Prints: **********
20 PRINT STRING$(5, 65)     ' Prints: AAAAA (ASCII 65 = A)
```

### STRIG
**Function/Statement**: Returns joystick button status or enables interrupts.

**Syntax**: 
- `STRIG(n)` - Function to read button
- `STRIG(n) ON/OFF/STOP` - Enable/disable interrupts

**Example**:
```basic
10 IF STRIG(0) THEN PRINT "Button 1 pressed"
20 STRIG(0) ON
30 ON STRIG(0) GOSUB 1000
```

### SWAP
**Statement**: Exchanges values of two variables.

**Syntax**: `SWAP variable1, variable2`

**Example**:
```basic
10 A = 10: B = 20
20 SWAP A, B
30 PRINT A, B          ' Prints: 20  10
```

### SYSTEM
**Statement**: Returns to operating system.

**Syntax**: `SYSTEM`

**Example**:
```basic
10 PRINT "Goodbye!"
20 SYSTEM
```

## T

### TAB
**Function**: Positions cursor to specified column in PRINT.

**Syntax**: `TAB(column)`

**Example**:
```basic
10 PRINT "Name:"; TAB(20); "John Doe"
20 PRINT "Age:"; TAB(20); "25"
```

### TAN
**Function**: Returns tangent of angle in radians.

**Syntax**: `TAN(numeric_expression)`

**Example**:
```basic
10 PRINT TAN(0)        ' Prints: 0
20 ANGLE = 3.14159 / 4 ' 45 degrees
30 PRINT TAN(ANGLE)    ' Prints: 1 (approximately)
```

### THEN
**Keyword**: Used with IF statements.

**Syntax**: `IF condition THEN statement(s)`

**Example**:
```basic
10 IF A > 5 THEN PRINT "Greater than 5"
```

### TIME$
**Function/Statement**: Gets or sets system time.

**Syntax**: 
- `TIME$` - Returns current time
- `TIME$ = time_string` - Sets time

**Example**:
```basic
10 PRINT "Current time: "; TIME$
20 TIME$ = "12:30:45"
```

### TIMER
**Function**: Returns seconds since midnight.

**Syntax**: `TIMER`

**Example**:
```basic
10 START_TIME = TIMER
20 ' ... some process ...
30 ELAPSED = TIMER - START_TIME
40 PRINT "Elapsed time:"; ELAPSED; "seconds"
```

### TO
**Keyword**: Used in FOR loops and GOTO ranges.

**Syntax**: `FOR variable = start TO end`

**Example**:
```basic
10 FOR I = 1 TO 10
```

### TROFF
**Statement**: Turns off program tracing.

**Syntax**: `TROFF`

**Example**:
```basic
10 TRON            ' Turn on tracing
20 ' ... traced code ...
30 TROFF           ' Turn off tracing
```

### TRON
**Statement**: Turns on program tracing.

**Syntax**: `TRON`

**Example**:
```basic
10 TRON            ' Show line numbers as executed
20 FOR I = 1 TO 5
30   PRINT I
40 NEXT I
50 TROFF
```

## U

### USR
**Function**: Calls machine language function.

**Syntax**: `USR[n](argument)`

**Example**:
```basic
10 DEF SEG = &H2000
20 RESULT = USR0(100)
```

### USING
**Keyword**: Used with PRINT for formatting.

**Syntax**: `PRINT USING format$; expression_list`

**Example**:
```basic
10 PRINT USING "##.##"; 3.14159
```

## V

### VAL
**Function**: Converts string to numeric value.

**Syntax**: `VAL(string_expression)`

**Example**:
```basic
10 A$ = "123.45"
20 NUMBER = VAL(A$)
30 PRINT NUMBER        ' Prints: 123.45
```

### VARPTR
**Function**: Returns memory address of variable.

**Syntax**: `VARPTR(variable)`

**Example**:
```basic
10 A = 100
20 ADDRESS = VARPTR(A)
30 PRINT "A is stored at:"; ADDRESS
```

### VIEW
**Statement**: Defines graphics viewport.

**Syntax**: `VIEW [[SCREEN] (x1,y1)-(x2,y2)[,color][,border]]`

**Example**:
```basic
10 SCREEN 1
20 VIEW (50,25)-(270,175), , 1  ' Define viewport with border
```

## W

### WAIT
**Statement**: Suspends execution until port condition is met.

**Syntax**: `WAIT port, and_expression[, xor_expression]`

**Example**:
```basic
10 WAIT 888, 1         ' Wait until bit 0 is set
```

### WEND
**Statement**: End of WHILE loop.

**Syntax**: 
```
WHILE condition
  [statements]
WEND
```

**Example**:
```basic
10 I = 1
20 WHILE I <= 10
30   PRINT I
40   I = I + 1
50 WEND
```

### WHILE
**Statement**: Beginning of WHILE loop.

**Syntax**: `WHILE condition`

**Example**:
```basic
10 WHILE NOT EOF(1)
20   INPUT #1, DATA$
30   PRINT DATA$
40 WEND
```

### WIDTH
**Statement**: Sets screen or printer width.

**Syntax**: `WIDTH [columns][,rows]` or `WIDTH device, columns`

**Example**:
```basic
10 WIDTH 40            ' Set screen to 40 columns
20 WIDTH 80, 25        ' Set 80x25 screen
30 WIDTH "LPT1:", 132  ' Set printer width
```

### WINDOW
**Statement**: Defines coordinate system for graphics.

**Syntax**: `WINDOW [[SCREEN] (x1,y1)-(x2,y2)]`

**Example**:
```basic
10 SCREEN 1
20 WINDOW (0,0)-(100,100)  ' Define logical coordinates
30 LINE (0,0)-(100,100)    ' Draw using logical coordinates
```

### WRITE
**Statement**: Writes data to screen or file in comma-delimited format.

**Syntax**: 
- `WRITE [expression_list]`
- `WRITE #file_number, expression_list`

**Example**:
```basic
10 WRITE "John", 25, "Engineer"  ' Prints: "John",25,"Engineer"
20 WRITE #1, A, B$, C            ' Write to file
```

## X

### XOR
**Operator**: Exclusive OR logical operator.

**Syntax**: `expression1 XOR expression2`

**Example**:
```basic
10 A = 5: B = 3
20 PRINT A XOR B       ' Bitwise XOR
30 IF (X=1) XOR (Y=1) THEN PRINT "Exactly one is true"
```

## Y

### (No commands begin with Y in GW-BASIC)

## Z

### (No commands begin with Z in GW-BASIC)

---

This completes the comprehensive commands reference for GW-BASIC. Each command includes syntax, description, and practical examples to help understand proper usage.
