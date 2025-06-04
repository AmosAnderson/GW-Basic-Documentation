# Troubleshooting

This section covers common issues encountered when programming in GW-BASIC, along with their solutions and prevention strategies.

## Error Messages and Solutions

### Syntax Errors

#### "Syntax Error"
**Cause**: Invalid command syntax, misspelled keywords, or incorrect punctuation.

**Examples**:
```basic
10 PINT "Hello"         ' Misspelled PRINT
20 FOR I = 1 TO 10:     ' Missing NEXT
30 IF A = 5 PRINT "Yes" ' Missing THEN
```

**Solutions**:
- Check spelling of all keywords
- Ensure proper statement structure
- Use LIST command to review suspicious lines
- Check for missing THEN, NEXT, WEND, etc.

#### "Unexpected End of Statement"
**Cause**: Missing operators, parentheses, or quotation marks.

**Examples**:
```basic
10 A = 5 +              ' Missing operand
20 PRINT "Hello         ' Missing closing quote
30 IF (A > 5 THEN       ' Missing closing parenthesis
```

**Solutions**:
- Count parentheses pairs
- Check all string literals have closing quotes
- Ensure all expressions are complete

### Runtime Errors

#### "Out of Memory"
**Error Code**: 7

**Causes**:
- Program too large
- Too many variables
- Arrays too large
- String space exhausted

**Solutions**:
```basic
' Check available memory
10 PRINT "String space:"; FRE(0)
20 PRINT "Total memory:"; FRE(-1)

' Clear unused variables
30 CLEAR

' Use smaller arrays
40 DIM ARRAY(100) ' Instead of ARRAY(10000)

' Free string space
50 TEMP$ = ""     ' Clear unused strings
```

#### "Subscript Out of Range"
**Error Code**: 9

**Cause**: Array index outside declared bounds.

**Examples**:
```basic
10 DIM A(10)            ' Array indices 0-10
20 A(15) = 5            ' Error: index 15 > 10
```

**Solutions**:
```basic
' Check array bounds before access
10 DIM SCORES(9)        ' Indices 0-9
20 FOR I = 0 TO 9       ' Stay within bounds
30   SCORES(I) = I * 10
40 NEXT I

' Use variables for bounds checking
50 MAX.INDEX = 9
60 IF INDEX <= MAX.INDEX THEN SCORES(INDEX) = VALUE
```

#### "Division by Zero"
**Error Code**: 11

**Cause**: Attempting to divide by zero or very small numbers.

**Solutions**:
```basic
' Check divisor before division
10 INPUT "Enter divisor: "; B
20 IF B = 0 THEN
30   PRINT "Cannot divide by zero"
40 ELSE
50   RESULT = A / B
60   PRINT "Result:"; RESULT
70 END IF

' Use small epsilon for floating-point comparison
80 EPSILON = 1E-10
90 IF ABS(B) < EPSILON THEN PRINT "Divisor too small"
```

#### "Overflow"
**Error Code**: 6

**Cause**: Numeric result too large for variable type.

**Examples**:
```basic
10 A% = 32767           ' Maximum integer
20 A% = A% + 1          ' Causes overflow
```

**Solutions**:
```basic
' Use appropriate data types
10 A! = 32767           ' Use single-precision
20 A! = A! + 1          ' No overflow

' Check values before operations
30 IF A% < 32767 THEN A% = A% + 1 ELSE PRINT "Would overflow"

' Use double-precision for large calculations
40 LARGE# = 1E20
50 RESULT# = LARGE# * LARGE#
```

#### "Type Mismatch"
**Error Code**: 13

**Cause**: Using wrong data type for operation.

**Examples**:
```basic
10 A$ = "Hello"
20 B = A$ + 5           ' Can't add number to string
```

**Solutions**:
```basic
' Use proper type conversion
10 A$ = "123"
20 B = VAL(A$) + 5      ' Convert string to number

' Check variable types
30 IF A$ = "" THEN A$ = "0"  ' Ensure string isn't empty
40 IF VAL(A$) = 0 AND A$ <> "0" THEN PRINT "Not a number"
```

### File I/O Errors

#### "File Not Found"
**Error Code**: 53

**Cause**: Attempting to open non-existent file.

**Solutions**:
```basic
' Use error trapping
10 ON ERROR GOTO 100
20 OPEN "DATA.TXT" FOR INPUT AS #1
30 ' File operations here
40 CLOSE #1
50 ON ERROR GOTO 0
60 END
100 IF ERR = 53 THEN
110   PRINT "File DATA.TXT not found"
120   PRINT "Creating new file..."
130   OPEN "DATA.TXT" FOR OUTPUT AS #1
140   CLOSE #1
150   RESUME 20
160 END IF
```

#### "Bad File Name"
**Error Code**: 64

**Cause**: Invalid filename or path.

**Solutions**:
```basic
' Validate filename
10 INPUT "Enter filename: "; F$
20 IF LEN(F$) = 0 THEN PRINT "Filename cannot be empty": GOTO 10
30 IF INSTR(F$, " ") > 0 THEN PRINT "No spaces in filename": GOTO 10
40 ' Proceed with file operation
```

#### "File Already Open"
**Error Code**: 55

**Cause**: Attempting to open file that's already open.

**Solutions**:
```basic
' Close file before reopening
10 CLOSE #1                 ' Close if open
20 OPEN "DATA.TXT" FOR INPUT AS #1

' Use different file numbers
30 OPEN "FILE1.TXT" FOR INPUT AS #1
40 OPEN "FILE2.TXT" FOR OUTPUT AS #2
```

## Memory Management Issues

### String Space Problems

**Symptoms**:
- "Out of String Space" errors
- Program slowing down
- Unexpected crashes

**Causes**:
- Too many string operations
- String concatenation in loops
- Large temporary strings

**Solutions**:
```basic
' Efficient string handling
10 REM Bad: Creates many temporary strings
20 RESULT$ = ""
30 FOR I = 1 TO 1000
40   RESULT$ = RESULT$ + STR$(I)  ' Memory leak
50 NEXT I

60 REM Better: Pre-allocate or use arrays
70 DIM PARTS$(1000)
80 FOR I = 1 TO 1000
90   PARTS$(I) = STR$(I)
100 NEXT I

' Force garbage collection
110 TEMP$ = STRING$(1000, "X")
120 TEMP$ = ""              ' Release memory
130 PRINT FRE(0)            ' Check available space
```

### Variable Storage Optimization

**Tips**:
```basic
' Use appropriate variable types
10 DEFINT A-F               ' Make A-F default to integer
20 DEFSNG G-M               ' G-M single-precision
30 DEFSTR N-Z               ' N-Z strings

' Minimize variable usage
40 REM Bad: Too many variables
50 A = 5: B = 10: C = 15: D = A + B + C

60 REM Better: Reuse variables
70 TOTAL = 5 + 10 + 15
```

## Graphics and Screen Issues

### Graphics Mode Problems

**Issue**: Graphics commands not working
**Cause**: Wrong screen mode

**Solution**:
```basic
10 SCREEN 1                 ' Set graphics mode first
20 CIRCLE (160, 100), 50    ' Now graphics work
30 SCREEN 0                 ' Return to text mode
```

**Issue**: Colors not displaying correctly
**Cause**: Monitor or adapter limitations

**Solutions**:
```basic
' Check available colors for mode
10 SCREEN 1                 ' CGA 4-color mode
20 FOR C = 0 TO 3          ' Only colors 0-3 available
30   PSET (C * 80, 100), C
40 NEXT C

' Use appropriate screen mode
50 SCREEN 2                 ' Monochrome high resolution
60 SCREEN 1                 ' Color medium resolution
```

### Screen Display Issues

**Issue**: Text wrapping incorrectly
**Solution**:
```basic
' Set proper screen width
10 WIDTH 80                 ' 80-column mode
20 WIDTH 40                 ' 40-column mode

' Control line length
30 TEXT$ = "Long line of text that might wrap"
40 IF LEN(TEXT$) > 40 THEN
50   PRINT LEFT$(TEXT$, 40)
60   PRINT MID$(TEXT$, 41)
70 ELSE
80   PRINT TEXT$
90 END IF
```

## Performance Issues

### Slow Program Execution

**Causes and Solutions**:

#### Inefficient Loops
```basic
' Bad: Nested string operations
10 FOR I = 1 TO 1000
20   FOR J = 1 TO 100
30     A$ = A$ + "X"       ' Very slow
40   NEXT J
50 NEXT I

' Better: Minimize string operations
60 CHUNK$ = STRING$(100, "X")
70 FOR I = 1 TO 1000
80   A$ = A$ + CHUNK$      ' Much faster
90 NEXT I
```

#### Unnecessary Calculations
```basic
' Bad: Recalculating constants
10 FOR I = 1 TO 1000
20   AREA = 3.14159 * R * R  ' Recalculates PI each time
30 NEXT I

' Better: Calculate once
40 PI = 3.14159
50 FOR I = 1 TO 1000
60   AREA = PI * R * R      ' Use precalculated value
70 NEXT I
```

#### Use Integer Math When Possible
```basic
' Slower: Floating-point
10 FOR I = 1 TO 1000
20   RESULT = I * 2.5
30 NEXT I

' Faster: Integer when appropriate
40 FOR I% = 1 TO 1000
50   RESULT% = I% * 2      ' Integer math is faster
60 NEXT I%
```

## Program Organization Issues

### Line Number Management

**Problem**: Running out of line numbers
**Solution**:
```basic
' Use RENUM command
RENUM 100, 10, 5            ' Start at 100, increment by 5

' Plan line numbering
' 1000-1999: Main program
' 2000-2999: Subroutines
' 3000-3999: Error handling
' 9000-9999: Data statements
```

### Subroutine Stack Overflow

**Problem**: Too many nested GOSUB calls
**Solution**:
```basic
' Bad: Deep nesting
10 GOSUB 100
' ...
100 GOSUB 200
200 GOSUB 300
300 GOSUB 400              ' Stack can overflow

' Better: Use structured approach
10 CALL.LEVEL = 1
20 GOSUB 1000              ' Main routine
30 END

1000 REM Main processing routine
1010 ' Do work here
1020 RETURN
```

## Debugging Techniques

### Program Tracing
```basic
' Turn on execution tracing
10 TRON                    ' Shows line numbers as executed
20 FOR I = 1 TO 5
30   PRINT I
40 NEXT I
50 TROFF                   ' Turn off tracing
```

### Variable Monitoring
```basic
' Insert debug prints
10 A = 5: B = 10
20 PRINT "DEBUG: A ="; A; "B ="; B    ' Check values
30 C = A + B
40 PRINT "DEBUG: C ="; C
```

### Selective Execution
```basic
' Use flags for debugging sections
10 DEBUG.MODE = 1          ' Set to 0 for normal run
20 IF DEBUG.MODE THEN PRINT "Starting main loop"
30 FOR I = 1 TO 100
40   IF DEBUG.MODE AND I MOD 10 = 0 THEN PRINT "Processing"; I
50   ' Main processing here
60 NEXT I
```

## Hardware Compatibility Issues

### Sound Problems
```basic
' Check if sound is working
10 SOUND 440, 18.2         ' A note for 1 second
20 INPUT "Did you hear a sound (Y/N)"; A$
30 IF UCASE$(A$) = "N" THEN PRINT "Sound system not working"
```

### Printer Issues
```basic
' Test printer availability
10 ON ERROR GOTO 100
20 LPRINT "Test line"
30 PRINT "Printer OK"
40 ON ERROR GOTO 0
50 END
100 PRINT "Printer error: "; ERR
110 RESUME 50
```

### Disk Drive Problems
```basic
' Check disk availability
10 ON ERROR GOTO 100
20 OPEN "TEST.TMP" FOR OUTPUT AS #1
30 PRINT #1, "Test"
40 CLOSE #1
50 KILL "TEST.TMP"
60 PRINT "Disk drive OK"
70 END
100 PRINT "Disk error: "; ERR
110 RESUME 70
```

## General Troubleshooting Tips

### Before Running Programs
1. **Check syntax**: Use LIST to review code
2. **Plan memory usage**: Consider array sizes and string space
3. **Test incrementally**: Build and test in small parts
4. **Use meaningful variable names**: Avoid single letters for important data

### During Development
1. **Save frequently**: Use SAVE command regularly
2. **Test with sample data**: Use known inputs to verify outputs
3. **Handle edge cases**: Test with empty inputs, zero values, maximum values
4. **Use error trapping**: Implement ON ERROR GOTO for critical sections

### When Errors Occur
1. **Note the error number**: Use ERR to get specific error codes
2. **Check the line number**: Use ERL to find where error occurred
3. **List the problematic line**: Use LIST line_number
4. **Check variable values**: Add PRINT statements before the error line
5. **Test minimal cases**: Create simple test programs to isolate the problem

This troubleshooting guide covers the most common issues encountered in GW-BASIC programming and provides practical solutions for each problem type.
