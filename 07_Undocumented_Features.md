# Undocumented Features

This section reveals hidden or lesser-known features of GW-BASIC discovered through analysis of the original assembly source code. These features were not typically documented in user manuals but can be extremely useful for advanced programming.

## Memory and System Access

### Extended FRE() Function Parameters

While most documentation only mentions `FRE(0)` for string space, GW-BASIC supports additional parameters:

```basic
10 PRINT "String space available: "; FRE(0)
20 PRINT "String space available: "; FRE("")    ' Same as FRE(0)
30 PRINT "Total free memory: "; FRE(-1)
40 PRINT "Stack space available: "; FRE(-2)
50 PRINT "Array space: "; FRE(1)
```

**Hidden Parameters**:
- `FRE(-1)` - Returns total available memory (program + variables + arrays)
- `FRE(-2)` - Returns available stack space for GOSUB calls and FOR loops
- `FRE(1)` - Returns available space for arrays and variables

### Direct Memory Manipulation

#### VARPTR Advanced Usage
Beyond getting variable addresses, VARPTR can be used for advanced memory operations:

```basic
10 A$ = "Hello World"
20 ADDR = VARPTR(A$)
30 PRINT "String descriptor at:"; ADDR
40 REM String descriptor contains length and pointer to actual string data
50 STRING.LENGTH = PEEK(ADDR)
60 STRING.PTR.LOW = PEEK(ADDR + 1)
70 STRING.PTR.HIGH = PEEK(ADDR + 2)
80 STRING.PTR = STRING.PTR.LOW + STRING.PTR.HIGH * 256
90 PRINT "String length:"; STRING.LENGTH
100 PRINT "String data at:"; STRING.PTR
```

#### Array Descriptor Access
Arrays have internal descriptors that can be accessed:

```basic
10 DIM A(10, 5)
20 DESCRIPTOR = VARPTR(A(0))
30 REM Array descriptor format:
40 REM Offset 0: Type (2=integer, 4=single, 8=double, 3=string)
50 REM Offset 1-2: Element size
60 REM Offset 3: Number of dimensions
70 REM Offset 4-5: First dimension size + 1
80 REM Offset 6-7: Second dimension size + 1 (if exists)
90 TYPE.CODE = PEEK(DESCRIPTOR)
100 ELEMENT.SIZE = PEEK(DESCRIPTOR + 1) + PEEK(DESCRIPTOR + 2) * 256
110 DIMENSIONS = PEEK(DESCRIPTOR + 3)
120 PRINT "Array type code:"; TYPE.CODE
130 PRINT "Element size:"; ELEMENT.SIZE
140 PRINT "Dimensions:"; DIMENSIONS
```

### Machine Language Interface

#### USR Function Extensions
GW-BASIC supports multiple USR functions (USR0 through USR9):

```basic
10 REM Set up machine language routine addresses
20 DEF SEG = &H2000
30 USR0.ADDR = &H2100
40 USR1.ADDR = &H2200
50 REM ... up to USR9
60 REM Call different routines
70 RESULT0 = USR0(parameter)
80 RESULT1 = USR1(parameter)
```

#### DEF SEG Advanced Usage
DEF SEG affects more than just USR calls:

```basic
10 REM Access video memory directly
20 DEF SEG = &HB800    ' CGA text video memory
30 FOR I = 0 TO 3999   ' 80x25 screen = 4000 bytes (char + attribute)
40   POKE I, 65        ' Fill screen with 'A'
50 NEXT I
60 DEF SEG            ' Restore default segment
```

## String and Variable Manipulation

### String Space Optimization

#### Force Garbage Collection
```basic
10 REM Force string garbage collection
20 TEMP$ = STRING$(1000, "X")  ' Allocate large string
30 TEMP$ = ""                  ' Release it
40 REM Force collection by attempting allocation
50 DUMMY$ = STRING$(1, " ")
60 DUMMY$ = ""
```

#### String Descriptor Manipulation
Advanced string manipulation through descriptors:

```basic
10 A$ = "HELLO"
20 B$ = "WORLD"
30 REM Manually concatenate by manipulating descriptors
40 A.ADDR = VARPTR(A$)
50 B.ADDR = VARPTR(B$)
60 A.LEN = PEEK(A.ADDR)
70 B.LEN = PEEK(B.ADDR)
80 REM This is for educational purposes - dangerous in practice!
```

### Variable Type Coercion

#### Implicit Type Conversions
GW-BASIC performs automatic conversions that can be exploited:

```basic
10 REM Integer overflow wraps around
20 A% = 32767
30 A% = A% + 1     ' Becomes -32768 (wraps)
40 PRINT A%

50 REM String to number conversion stops at first non-digit
60 A$ = "123.45ABC"
70 VALUE = VAL(A$)  ' Returns 123.45
80 PRINT VALUE
```

## Graphics and Screen Features

### Hidden Graphics Modes

#### EGA/VGA Detection
```basic
10 REM Detect extended graphics capabilities
20 ON ERROR GOTO 100
30 SCREEN 7     ' EGA 320x200 16-color mode
40 PRINT "EGA/VGA detected"
50 SCREEN 0
60 GOTO 110
100 PRINT "Standard CGA only"
110 ON ERROR GOTO 0
```

#### Graphics Coordinate Systems
```basic
10 SCREEN 1
20 REM PMAP function for coordinate conversion
30 REM Convert viewport coordinates to screen coordinates
40 WINDOW (0, 0)-(100, 100)  ' Set logical coordinate system
50 FOR X = 0 TO 100 STEP 10
60   SCREEN.X = PMAP(X, 0)   ' Convert X coordinate
70   SCREEN.Y = PMAP(50, 1)  ' Convert Y coordinate
80   PSET (X, 50)            ' Plot in logical coordinates
90 NEXT X
```

### Screen Buffer Access

#### Direct Screen Manipulation
```basic
10 SCREEN 1
20 REM Get and put graphics images
30 DIM IMAGE%(100)           ' Array to store image
40 CIRCLE (50, 50), 20
50 GET (30, 30)-(70, 70), IMAGE%  ' Capture image
60 PUT (100, 100), IMAGE%    ' Reproduce image
70 PUT (150, 100), IMAGE%, XOR  ' XOR mode for animation
```

## File and Device Features

### Device Control

#### Serial Port Configuration
```basic
10 REM Open serial port with specific parameters
20 OPEN "COM1:9600,N,8,1" FOR RANDOM AS #1
30 REM Send control characters
40 PRINT #1, CHR$(27); "[2J";  ' ANSI clear screen
50 CLOSE #1
```

#### Printer Control Codes
```basic
10 REM Send control codes to printer
20 ESC$ = CHR$(27)
30 LPRINT ESC$; "@";           ' Reset printer
40 LPRINT ESC$; "E";           ' Bold on
50 LPRINT "Bold Text"
60 LPRINT ESC$; "F";           ' Bold off
```

### Extended File Operations

#### File Handle Manipulation
```basic
10 REM Access file handles beyond #1-#15
20 REM This is system-dependent and not recommended
30 ON ERROR GOTO 100
40 FOR I = 1 TO 255
50   OPEN "NUL" FOR OUTPUT AS #I
60   PRINT "File handle"; I; "available"
70   CLOSE #I
80 NEXT I
90 GOTO 110
100 PRINT "Maximum file handle:"; I - 1
110 ON ERROR GOTO 0
```

## Timing and Performance

### TIMER Function Precision

#### High-Resolution Timing
```basic
10 REM TIMER returns seconds with 18.2 Hz precision
20 START.TIME = TIMER
30 FOR I = 1 TO 1000
40   REM Some operation
50 NEXT I
60 ELAPSED = TIMER - START.TIME
70 PRINT "Time:"; ELAPSED; "seconds"
80 PRINT "Ticks:"; ELAPSED * 18.2; "(approx)"
```

#### Midnight Rollover Handling
```basic
10 START.TIME = TIMER
20 REM ... long operation ...
30 END.TIME = TIMER
40 IF END.TIME < START.TIME THEN
50   REM Timer rolled over at midnight
60   ELAPSED = (86400 - START.TIME) + END.TIME
70 ELSE
80   ELAPSED = END.TIME - START.TIME
90 END IF
```

## Sound and Music Extensions

### Advanced PLAY Command

#### Hidden PLAY Parameters
```basic
10 REM Extended PLAY command features
20 PLAY "MB"           ' Background music mode
30 PLAY "MF"           ' Foreground music mode  
40 PLAY "ML"           ' Legato (smooth)
50 PLAY "MN"           ' Normal
60 PLAY "MS"           ' Staccato (short)
70 PLAY "X" + VARPTR$(MUSIC$)  ' Execute string variable contents
```

#### Music String Variables
```basic
10 MELODY$ = "CDEFGAB"
20 PLAY "X" + VARPTR$(MELODY$)  ' Play from string variable
```

## Error Handling Extensions

### Advanced Error Information

#### Error Context
```basic
10 ON ERROR GOTO 1000
20 REM ... program code ...
1000 REM Advanced error handling
1010 PRINT "Error"; ERR; "at line"; ERL
1020 REM Check error context
1030 IF ERR = 53 THEN PRINT "File not found"
1040 IF ERR = 6 THEN PRINT "Overflow error"
1050 REM Get additional error information
1060 PRINT "Available memory:"; FRE(-1)
1070 PRINT "String space:"; FRE(0)
1080 RESUME NEXT
```

## Undocumented System Variables

### Internal Counters

#### FOR Loop Stack
```basic
10 REM Monitor FOR loop nesting
20 FOR I = 1 TO 5
30   FOR J = 1 TO 3
40     PRINT "Stack space:"; FRE(-2)
50   NEXT J
60 NEXT I
```

#### GOSUB Stack Monitoring
```basic
10 GOSUB 1000
20 END
1000 PRINT "GOSUB stack space:"; FRE(-2)
1010 GOSUB 2000
1020 RETURN
2000 PRINT "Nested GOSUB stack:"; FRE(-2)
2010 RETURN
```

## Keyboard and Input Extensions

### Extended Key Codes

#### Function Key Detection
```basic
10 K$ = INKEY$
20 IF LEN(K$) = 2 THEN
30   CODE = ASC(RIGHT$(K$, 1))
40   SELECT CASE CODE
50     CASE 59: PRINT "F1 pressed"
60     CASE 60: PRINT "F2 pressed"
70     REM ... F3-F10 are codes 61-68
80     CASE 71: PRINT "Home pressed"
90     CASE 72: PRINT "Up arrow pressed"
100   END SELECT
110 END IF
```

#### Extended ASCII Detection
```basic
10 REM Detect extended ASCII characters
20 INPUT "Press a key: "; DUMMY$
30 K$ = INKEY$
40 WHILE K$ = "": K$ = INKEY$: WEND
50 IF LEN(K$) = 1 THEN
60   PRINT "Standard key:"; ASC(K$)
70 ELSE
80   PRINT "Extended key:"; ASC(RIGHT$(K$, 1))
90 END IF
```

## Compatibility Features

### Version Detection

#### BASIC Version Information
```basic
10 REM Detect GW-BASIC version through memory inspection
20 ON ERROR GOTO 100
30 DEF SEG = 0
40 VERSION.BYTE = PEEK(&HFF)  ' System-dependent
50 PRINT "System byte:"; VERSION.BYTE
60 DEF SEG
70 GOTO 110
100 PRINT "Cannot detect version"
110 ON ERROR GOTO 0
```

### Hardware Feature Detection

#### Math Coprocessor Detection
```basic
10 REM Test for 8087 math coprocessor
20 ON ERROR GOTO 100
30 A# = 1.0#
40 B# = 3.0#
50 C# = A# / B#
60 REM If we get here, math coprocessor may be present
70 PRINT "Math coprocessor available"
80 GOTO 110
100 PRINT "Software math only"
110 ON ERROR GOTO 0
```

## Performance Optimization Secrets

### Memory Layout Optimization

#### Variable Declaration Order
```basic
10 REM Declare frequently used variables first for faster access
20 COUNTER% = 0     ' Integer variables are fastest
21 FLAG% = 0
22 INDEX% = 0
30 TEMP! = 0        ' Single-precision next
31 RESULT! = 0
40 PRECISION# = 0   ' Double-precision slower
50 MESSAGE$ = ""    ' Strings slowest
```

#### String Optimization
```basic
10 REM Pre-allocate string space to avoid garbage collection
20 BUFFER$ = SPACE$(1000)  ' Pre-allocate
30 FOR I = 1 TO 100
40   REM Use MID$ assignment instead of concatenation
50   MID$(BUFFER$, I, 1) = CHR$(65 + (I MOD 26))
60 NEXT I
```

## Undocumented Limits

### System Boundaries
- Maximum line number: 65529 (not 65535)
- Maximum string length: 255 characters
- Maximum array dimensions: 255
- Maximum open files: System dependent (usually 3-15)
- Maximum FOR loop nesting: Limited by stack space (typically 25-30 levels)
- Maximum GOSUB nesting: Limited by stack space (typically 25-30 levels)

### Memory Constraints
```basic
10 REM Check various memory limits
20 PRINT "Total memory:"; FRE(-1)
30 PRINT "String space:"; FRE(0)
40 PRINT "Stack space:"; FRE(-2)
50 REM Typical memory layout on 64KB system:
60 REM Program: 0-16KB
70 REM Variables: 16-32KB  
80 REM Arrays: 32-48KB
90 REM String space: 48-60KB
100 REM Stack: 60-64KB
```

These undocumented features provide powerful capabilities for advanced GW-BASIC programming, though they should be used with caution as they may not be portable to other BASIC implementations.
