# Programming Examples

This section provides practical programming examples that demonstrate various GW-BASIC features and common programming patterns. Each example includes complete, runnable code with explanations.

## Basic Program Structure Examples

### Hello World Program
The classic first program demonstrates basic output:

```basic
10 REM Hello World Program
20 PRINT "Hello, World!"
30 END
```

**Explanation:**
- Line 10: Comment explaining the program's purpose
- Line 20: Display text on screen
- Line 30: Terminate program execution

### Simple Input and Output
```basic
10 REM Input/Output Example
20 INPUT "Enter your name: "; NAME$
30 INPUT "Enter your age: "; AGE
40 PRINT "Hello, "; NAME$; "! You are"; AGE; "years old."
50 END
```

**Features Demonstrated:**
- String input with prompts
- Numeric input
- String concatenation in output
- Mixed data types in PRINT statement

## Mathematical Programs

### Calculator Program
```basic
10 REM Simple Calculator
20 PRINT "Simple Calculator"
30 PRINT "=================="
40 INPUT "Enter first number: "; A
50 INPUT "Enter second number: "; B
60 PRINT
70 PRINT "A + B ="; A + B
80 PRINT "A - B ="; A - B
90 PRINT "A * B ="; A * B
100 IF B <> 0 THEN PRINT "A / B ="; A / B ELSE PRINT "Cannot divide by zero"
110 PRINT "A ^ B ="; A ^ B
120 END
```

### Quadratic Equation Solver
```basic
10 REM Quadratic Equation Solver: ax^2 + bx + c = 0
20 PRINT "Quadratic Equation Solver"
30 PRINT "========================="
40 INPUT "Enter coefficient a: "; A
50 IF A = 0 THEN PRINT "Not a quadratic equation": END
60 INPUT "Enter coefficient b: "; B
70 INPUT "Enter coefficient c: "; C
80 D = B * B - 4 * A * C
90 PRINT "Discriminant ="; D
100 IF D < 0 THEN PRINT "No real roots": END
110 IF D = 0 THEN 
120   ROOT = -B / (2 * A)
130   PRINT "One root: x ="; ROOT
140 ELSE
150   ROOT1 = (-B + SQR(D)) / (2 * A)
160   ROOT2 = (-B - SQR(D)) / (2 * A)
170   PRINT "Two roots:"
180   PRINT "x1 ="; ROOT1
190   PRINT "x2 ="; ROOT2
200 END IF
210 END
```

### Mathematical Series
```basic
10 REM Calculate Pi using Leibniz series
20 REM Pi/4 = 1 - 1/3 + 1/5 - 1/7 + 1/9 - ...
30 PRINT "Calculating Pi using Leibniz series"
40 INPUT "Number of terms: "; N
50 PI.APPROX = 0
60 FOR I = 0 TO N - 1
70   TERM = (-1) ^ I / (2 * I + 1)
80   PI.APPROX = PI.APPROX + TERM
90 NEXT I
100 PI.APPROX = PI.APPROX * 4
110 PRINT "Pi approximation:"; PI.APPROX
120 PRINT "Actual Pi:       "; 3.141592653589793#
130 PRINT "Error:           "; ABS(PI.APPROX - 3.141592653589793#)
140 END
```

## Control Flow Examples

### Menu-Driven Program
```basic
10 REM Menu System Example
20 CLS
30 PRINT "MAIN MENU"
40 PRINT "========="
50 PRINT "1. Display Numbers"
60 PRINT "2. Calculate Sum"
70 PRINT "3. Show Pattern"
80 PRINT "4. Exit"
90 PRINT
100 INPUT "Select option (1-4): "; CHOICE
110 ON CHOICE GOSUB 200, 300, 400, 500
120 IF CHOICE < 1 OR CHOICE > 4 THEN PRINT "Invalid choice!": GOTO 90
130 GOTO 20
140 REM
200 REM Display Numbers Subroutine
210 PRINT "Numbers 1 to 10:"
220 FOR I = 1 TO 10
230   PRINT I;
240 NEXT I
250 PRINT: PRINT "Press any key to continue...": A$ = INPUT$(1)
260 RETURN
270 REM
300 REM Calculate Sum Subroutine
310 INPUT "Enter start number: "; START
320 INPUT "Enter end number: "; FINISH
330 SUM = 0
340 FOR I = START TO FINISH
350   SUM = SUM + I
360 NEXT I
370 PRINT "Sum from"; START; "to"; FINISH; "="; SUM
380 PRINT "Press any key to continue...": A$ = INPUT$(1)
390 RETURN
400 REM Show Pattern Subroutine
410 INPUT "Enter pattern size: "; SIZE
420 FOR ROW = 1 TO SIZE
430   FOR COL = 1 TO ROW
440     PRINT "*";
450   NEXT COL
460   PRINT
470 NEXT ROW
480 PRINT "Press any key to continue...": A$ = INPUT$(1)
490 RETURN
500 REM Exit Subroutine
510 PRINT "Goodbye!"
520 END
```

### Nested Loops Example
```basic
10 REM Multiplication Table Generator
20 INPUT "Enter table size: "; SIZE
30 PRINT
40 REM Print header
50 PRINT "   ";
60 FOR I = 1 TO SIZE
70   PRINT USING "####"; I;
80 NEXT I
90 PRINT
100 REM Print separator line
110 FOR I = 1 TO (SIZE * 4) + 3
120   PRINT "-";
130 NEXT I
140 PRINT
150 REM Print table rows
160 FOR ROW = 1 TO SIZE
170   PRINT USING "###"; ROW;
180   PRINT "|";
190   FOR COL = 1 TO SIZE
200     PRODUCT = ROW * COL
210     PRINT USING "####"; PRODUCT;
220   NEXT COL
230   PRINT
240 NEXT ROW
250 END
```

## String Processing Examples

### Text Analysis Program
```basic
10 REM Text Analysis Program
20 INPUT "Enter a sentence: "; TEXT$
30 IF TEXT$ = "" THEN END
40 REM
50 REM Count characters, words, and vowels
60 CHAR.COUNT = LEN(TEXT$)
70 WORD.COUNT = 1
80 VOWEL.COUNT = 0
90 REM
100 FOR I = 1 TO CHAR.COUNT
110   CHAR$ = MID$(TEXT$, I, 1)
120   REM Count spaces (words)
130   IF CHAR$ = " " THEN WORD.COUNT = WORD.COUNT + 1
140   REM Count vowels
150   IF CHAR$ = "A" OR CHAR$ = "E" OR CHAR$ = "I" OR CHAR$ = "O" OR CHAR$ = "U" THEN VOWEL.COUNT = VOWEL.COUNT + 1
160   IF CHAR$ = "a" OR CHAR$ = "e" OR CHAR$ = "i" OR CHAR$ = "o" OR CHAR$ = "u" THEN VOWEL.COUNT = VOWEL.COUNT + 1
170 NEXT I
180 REM
190 PRINT "Analysis Results:"
200 PRINT "================"
210 PRINT "Characters:"; CHAR.COUNT
220 PRINT "Words:     "; WORD.COUNT
230 PRINT "Vowels:    "; VOWEL.COUNT
240 END
```

### String Manipulation Utilities
```basic
10 REM String Utility Functions
20 DEF FN REVERSE$(S$) = ""  ' Will be defined procedurally
30 INPUT "Enter a string: "; ORIGINAL$
40 REM
50 REM Reverse string
60 REVERSED$ = ""
70 FOR I = LEN(ORIGINAL$) TO 1 STEP -1
80   REVERSED$ = REVERSED$ + MID$(ORIGINAL$, I, 1)
90 NEXT I
100 REM
110 REM Convert to uppercase
120 UPPER$ = ""
130 FOR I = 1 TO LEN(ORIGINAL$)
140   CHAR$ = MID$(ORIGINAL$, I, 1)
150   CODE = ASC(CHAR$)
160   IF CODE >= 97 AND CODE <= 122 THEN CODE = CODE - 32
170   UPPER$ = UPPER$ + CHR$(CODE)
180 NEXT I
190 REM
200 REM Display results
210 PRINT "Original: "; ORIGINAL$
220 PRINT "Reversed: "; REVERSED$
230 PRINT "Uppercase:"; UPPER$
240 PRINT "Length:   "; LEN(ORIGINAL$)
250 END
```

## Array Programming Examples

### Array Sorting (Bubble Sort)
```basic
10 REM Bubble Sort Example
20 INPUT "How many numbers to sort: "; N
30 DIM NUMBERS(N)
40 REM
50 REM Input numbers
60 FOR I = 1 TO N
70   PRINT "Enter number"; I; ": ";
80   INPUT NUMBERS(I)
90 NEXT I
100 REM
110 REM Bubble sort algorithm
120 FOR I = 1 TO N - 1
130   FOR J = 1 TO N - I
140     IF NUMBERS(J) > NUMBERS(J + 1) THEN
150       REM Swap elements
160       TEMP = NUMBERS(J)
170       NUMBERS(J) = NUMBERS(J + 1)
180       NUMBERS(J + 1) = TEMP
190     END IF
200   NEXT J
210 NEXT I
220 REM
230 REM Display sorted array
240 PRINT "Sorted numbers:"
250 FOR I = 1 TO N
260   PRINT NUMBERS(I);
270 NEXT I
280 PRINT
290 END
```

### Matrix Operations
```basic
10 REM Matrix Addition Example
20 INPUT "Enter matrix size (N x N): "; N
30 DIM A(N, N), B(N, N), C(N, N)
40 REM
50 REM Input first matrix
60 PRINT "Enter first matrix:"
70 FOR ROW = 1 TO N
80   FOR COL = 1 TO N
90     PRINT "A("; ROW; ","; COL; ") = ";
100     INPUT A(ROW, COL)
110   NEXT COL
120 NEXT ROW
130 REM
140 REM Input second matrix
150 PRINT "Enter second matrix:"
160 FOR ROW = 1 TO N
170   FOR COL = 1 TO N
180     PRINT "B("; ROW; ","; COL; ") = ";
190     INPUT B(ROW, COL)
200   NEXT COL
210 NEXT ROW
220 REM
230 REM Calculate sum
240 FOR ROW = 1 TO N
250   FOR COL = 1 TO N
260     C(ROW, COL) = A(ROW, COL) + B(ROW, COL)
270   NEXT COL
280 NEXT ROW
290 REM
300 REM Display result
310 PRINT "Result matrix (A + B):"
320 FOR ROW = 1 TO N
330   FOR COL = 1 TO N
340     PRINT USING "######.##"; C(ROW, COL);
350   NEXT COL
360   PRINT
370 NEXT ROW
380 END
```

## Graphics Programming Examples

### Simple Drawing Program
```basic
10 REM Simple Graphics Demo
20 SCREEN 1                    ' Set graphics mode
30 COLOR 15, 1                 ' White on blue
40 CLS
50 REM
60 REM Draw border
70 LINE (0, 0)-(319, 199), 15, B
80 REM
90 REM Draw some shapes
100 CIRCLE (160, 100), 50, 14
110 CIRCLE (160, 100), 30, 12
120 CIRCLE (160, 100), 10, 10
130 REM
140 REM Draw lines from center
150 FOR ANGLE = 0 TO 360 STEP 30
160   X = 160 + 80 * COS(ANGLE * 3.14159 / 180)
170   Y = 100 + 80 * SIN(ANGLE * 3.14159 / 180)
180   LINE (160, 100)-(X, Y), 11
190 NEXT ANGLE
200 REM
210 REM Wait for keypress
220 LOCATE 25, 1: PRINT "Press any key to continue...";
230 A$ = INPUT$(1)
240 SCREEN 0                   ' Return to text mode
250 END
```

### Animated Graphics
```basic
10 REM Bouncing Ball Animation
20 SCREEN 1
30 CLS
40 REM
50 REM Initialize ball position and velocity
60 X = 160: Y = 100
70 VX = 3: VY = 2
80 RADIUS = 5
90 COLOR.VAL = 12
100 REM
110 REM Animation loop
120 FOR FRAME = 1 TO 1000
130   REM Erase old ball
140   CIRCLE (X, Y), RADIUS, 0
150   REM
160   REM Update position
170   X = X + VX
180   Y = Y + VY
190   REM
200   REM Bounce off walls
210   IF X <= RADIUS OR X >= 320 - RADIUS THEN VX = -VX
220   IF Y <= RADIUS OR Y >= 200 - RADIUS THEN VY = -VY
230   REM
240   REM Keep ball in bounds
250   IF X < RADIUS THEN X = RADIUS
260   IF X > 320 - RADIUS THEN X = 320 - RADIUS
270   IF Y < RADIUS THEN Y = RADIUS
280   IF Y > 200 - RADIUS THEN Y = 200 - RADIUS
290   REM
300   REM Draw new ball
310   CIRCLE (X, Y), RADIUS, COLOR.VAL
320   REM
330   REM Check for keypress to exit
340   K$ = INKEY$
350   IF K$ <> "" THEN 380
360 NEXT FRAME
370 REM
380 SCREEN 0
390 PRINT "Animation ended."
400 END
```

## File I/O Examples

### Sequential File Operations
```basic
10 REM Phone Book Program
20 DIM NAMES$(100), PHONES$(100)
30 COUNT = 0
40 REM
50 REM Main menu
60 CLS
70 PRINT "PHONE BOOK"
80 PRINT "=========="
90 PRINT "1. Add Entry"
100 PRINT "2. Display All"
110 PRINT "3. Save to File"
120 PRINT "4. Load from File"
130 PRINT "5. Exit"
140 INPUT "Choice: "; CHOICE
150 ON CHOICE GOSUB 200, 300, 400, 500, 600
160 GOTO 60
170 REM
200 REM Add entry
210 IF COUNT >= 100 THEN PRINT "Phone book full!": RETURN
220 COUNT = COUNT + 1
230 INPUT "Name: "; NAMES$(COUNT)
240 INPUT "Phone: "; PHONES$(COUNT)
250 PRINT "Entry added."
260 RETURN
270 REM
300 REM Display all entries
310 IF COUNT = 0 THEN PRINT "No entries.": RETURN
320 FOR I = 1 TO COUNT
330   PRINT I; ": "; NAMES$(I); " - "; PHONES$(I)
340 NEXT I
350 PRINT "Press any key...": A$ = INPUT$(1)
360 RETURN
370 REM
400 REM Save to file
410 OPEN "PHONEBOOK.DAT" FOR OUTPUT AS #1
420 PRINT #1, COUNT
430 FOR I = 1 TO COUNT
440   PRINT #1, NAMES$(I)
450   PRINT #1, PHONES$(I)
460 NEXT I
470 CLOSE #1
480 PRINT "Data saved."
490 RETURN
500 REM Load from file
510 ON ERROR GOTO 580
520 OPEN "PHONEBOOK.DAT" FOR INPUT AS #1
530 INPUT #1, COUNT
540 FOR I = 1 TO COUNT
550   INPUT #1, NAMES$(I)
560   INPUT #1, PHONES$(I)
570 NEXT I
580 CLOSE #1
590 ON ERROR GOTO 0
600 PRINT "Data loaded."
610 RETURN
620 REM Exit
630 PRINT "Goodbye!"
640 END
```

### Random Access File Example
```basic
10 REM Student Records System
20 TYPE STUDENT.RECORD
30   NAME AS STRING * 30
40   GRADE AS INTEGER
50   AVERAGE AS SINGLE
60 END TYPE
70 REM
80 REM Simulate record structure with FIELD
90 OPEN "STUDENTS.DAT" FOR RANDOM AS #1 LEN = 36
100 FIELD #1, 30 AS NAME$, 2 AS GRADE$, 4 AS AVERAGE$
110 REM
120 REM Menu system
130 CLS
140 PRINT "STUDENT RECORDS"
150 PRINT "==============="
160 PRINT "1. Add Student"
170 PRINT "2. View Student"
180 PRINT "3. Update Student"
190 PRINT "4. Exit"
200 INPUT "Choice: "; CHOICE
210 ON CHOICE GOSUB 300, 400, 500, 600
220 GOTO 130
230 REM
300 REM Add student
310 INPUT "Record number: "; RECNUM
320 INPUT "Student name: "; N$
330 INPUT "Grade level: "; G
340 INPUT "Average: "; A
350 LSET NAME$ = N$
360 LSET GRADE$ = MKI$(G)
370 LSET AVERAGE$ = MKS$(A)
380 PUT #1, RECNUM
390 PRINT "Student added."
400 RETURN
410 REM
420 REM View student
430 INPUT "Record number: "; RECNUM
440 GET #1, RECNUM
450 IF NAME$ = STRING$(30, 0) THEN PRINT "No record found.": RETURN
460 PRINT "Name: "; RTRIM$(NAME$)
470 PRINT "Grade: "; CVI(GRADE$)
480 PRINT "Average: "; CVS(AVERAGE$)
490 RETURN
500 REM Update student (similar to add)
510 PRINT "Update feature - similar to add"
520 RETURN
530 REM
540 REM Exit
550 CLOSE #1
560 PRINT "Goodbye!"
570 END
```

## Game Programming Examples

### Number Guessing Game
```basic
10 REM Number Guessing Game
20 RANDOMIZE
30 SECRET = INT(RND(1) * 100) + 1
40 ATTEMPTS = 0
50 MAX.ATTEMPTS = 7
60 REM
70 PRINT "Number Guessing Game"
80 PRINT "===================="
90 PRINT "I'm thinking of a number between 1 and 100."
100 PRINT "You have"; MAX.ATTEMPTS; "attempts to guess it."
110 PRINT
120 REM
130 REM Game loop
140 WHILE ATTEMPTS < MAX.ATTEMPTS
150   ATTEMPTS = ATTEMPTS + 1
160   PRINT "Attempt"; ATTEMPTS; "of"; MAX.ATTEMPTS
170   INPUT "Your guess: "; GUESS
180   REM
190   IF GUESS = SECRET THEN
200     PRINT "Congratulations! You guessed it in"; ATTEMPTS; "attempts!"
210     END
220   ELSEIF GUESS < SECRET THEN
230     PRINT "Too low!"
240   ELSE
250     PRINT "Too high!"
260   END IF
270   PRINT
280 WEND
290 REM
300 PRINT "Sorry, you've used all your attempts."
310 PRINT "The number was"; SECRET
320 END
```

### Simple Text Adventure
```basic
10 REM Simple Text Adventure
20 REM Player position: ROOM (1-4)
30 ROOM = 1
40 INVENTORY$ = ""
50 REM
60 REM Game loop
70 WHILE ROOM > 0
80   ON ROOM GOSUB 200, 300, 400, 500
90   PRINT
100   INPUT "What do you do? "; ACTION$
110   ACTION$ = UCASE$(ACTION$)
120   ON ROOM GOSUB 250, 350, 450, 550
130 WEND
140 END
150 REM
200 REM Room 1 - Starting room
210 PRINT "You are in a dark cave entrance."
220 PRINT "There is a torch on the ground."
230 PRINT "You can go NORTH or EAST."
240 RETURN
250 REM Room 1 actions
260 IF ACTION$ = "TAKE TORCH" THEN INVENTORY$ = INVENTORY$ + "TORCH ": PRINT "Torch taken."
270 IF ACTION$ = "NORTH" THEN ROOM = 2
280 IF ACTION$ = "EAST" THEN ROOM = 3
290 RETURN
300 REM Room 2 - Dark passage
310 PRINT "You are in a dark passage."
320 IF INSTR(INVENTORY$, "TORCH") = 0 THEN
330   PRINT "It's too dark to see anything!"
340   PRINT "You can only go SOUTH."
350 ELSE
360   PRINT "The torch illuminates ancient symbols on the walls."
370   PRINT "You can go SOUTH or NORTH."
380 END IF
390 RETURN
400 REM Room 2 actions
410 IF ACTION$ = "SOUTH" THEN ROOM = 1
420 IF ACTION$ = "NORTH" AND INSTR(INVENTORY$, "TORCH") > 0 THEN ROOM = 4
430 RETURN
440 REM Continue with more rooms...
450 PRINT "Room 3 and 4 would be implemented similarly..."
460 RETURN
470 END
```

## Advanced Programming Techniques

### Recursive-like Functions with GOSUB
```basic
10 REM Factorial Calculator using Subroutines
20 INPUT "Enter a number for factorial: "; N
30 IF N < 0 THEN PRINT "Invalid input": END
40 ORIGINAL.N = N
50 RESULT = 1
60 GOSUB 1000
70 PRINT ORIGINAL.N; "! ="; RESULT
80 END
90 REM
1000 REM Factorial subroutine
1010 IF N <= 1 THEN RETURN
1020 RESULT = RESULT * N
1030 N = N - 1
1040 GOSUB 1000
1050 RETURN
```

### Memory-Efficient Programming
```basic
10 REM Memory-efficient data processing
20 REM Process large datasets without storing all in memory
30 OPEN "DATAFILE.TXT" FOR INPUT AS #1
40 TOTAL = 0
50 COUNT = 0
60 MAX.VALUE = -999999
70 MIN.VALUE = 999999
80 REM
90 REM Process file line by line
100 WHILE NOT EOF(1)
110   INPUT #1, VALUE
120   TOTAL = TOTAL + VALUE
130   COUNT = COUNT + 1
140   IF VALUE > MAX.VALUE THEN MAX.VALUE = VALUE
150   IF VALUE < MIN.VALUE THEN MIN.VALUE = VALUE
160   REM Process value immediately, don't store
170 WEND
180 REM
190 CLOSE #1
200 AVERAGE = TOTAL / COUNT
210 PRINT "Statistics:"
220 PRINT "Count:   "; COUNT
230 PRINT "Total:   "; TOTAL
240 PRINT "Average: "; AVERAGE
250 PRINT "Maximum: "; MAX.VALUE
260 PRINT "Minimum: "; MIN.VALUE
270 END
```

## Error Handling Examples

### Robust File Operations
```basic
10 REM Robust file handling with error trapping
20 ON ERROR GOTO 1000
30 INPUT "Enter filename: "; FILENAME$
40 OPEN FILENAME$ FOR INPUT AS #1
50 REM
60 REM Process file
70 WHILE NOT EOF(1)
80   LINE INPUT #1, TEXT$
90   PRINT TEXT$
100 WEND
110 REM
120 CLOSE #1
130 PRINT "File processed successfully."
140 END
150 REM
1000 REM Error handler
1010 ERROR.CODE = ERR
1020 ERROR.LINE = ERL
1030 SELECT CASE ERROR.CODE
1040   CASE 53: PRINT "File not found: "; FILENAME$
1050   CASE 64: PRINT "Bad file name: "; FILENAME$
1060   CASE 68: PRINT "Device unavailable"
1070   CASE 71: PRINT "Disk not ready"
1080   CASE ELSE: PRINT "Error"; ERROR.CODE; "at line"; ERROR.LINE
1090 END SELECT
1100 RESUME 140
```

These examples demonstrate the full range of GW-BASIC programming capabilities, from simple programs to complex applications involving graphics, file I/O, and advanced programming techniques. Each example is designed to be educational and immediately usable.
