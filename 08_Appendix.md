# Appendix

## A. Error Codes Reference

GW-BASIC uses numeric error codes to identify specific error conditions. Here is a comprehensive list:

| Code | Error Message | Description |
|------|---------------|-------------|
| 1 | NEXT without FOR | NEXT statement without corresponding FOR |
| 2 | Syntax error | Invalid program statement syntax |
| 3 | RETURN without GOSUB | RETURN statement without GOSUB |
| 4 | Out of DATA | READ statement when no DATA available |
| 5 | Illegal function call | Invalid parameter or function usage |
| 6 | Overflow | Numeric result too large for variable type |
| 7 | Out of memory | Insufficient memory for operation |
| 8 | Undefined line number | GOTO/GOSUB to non-existent line |
| 9 | Subscript out of range | Array index outside declared bounds |
| 10 | Duplicate definition | Array or function redefined |
| 11 | Division by zero | Attempted division by zero |
| 12 | Illegal direct | Statement not allowed in immediate mode |
| 13 | Type mismatch | Wrong data type for operation |
| 14 | Out of string space | String memory exhausted |
| 15 | String too long | String exceeds 255 characters |
| 16 | String formula too complex | Too many string operations |
| 17 | Can't continue | CONT not possible |
| 18 | Undefined user function | DEF FN function not defined |
| 19 | No RESUME | Error handler missing RESUME |
| 20 | RESUME without error | RESUME outside error handler |
| 22 | Missing operand | Expression incomplete |
| 24 | Device timeout | I/O device not responding |
| 25 | Device fault | Hardware device error |
| 26 | FOR without NEXT | FOR loop not closed |
| 27 | Out of paper | Printer out of paper |
| 29 | WHILE without WEND | WHILE loop not closed |
| 30 | WEND without WHILE | WEND without WHILE |
| 50 | FIELD overflow | FIELD statement buffer overflow |
| 51 | Internal error | System internal error |
| 52 | Bad file number | Invalid file handle |
| 53 | File not found | Specified file doesn't exist |
| 54 | Bad file mode | Invalid file access mode |
| 55 | File already open | File already opened |
| 57 | Device I/O error | General device error |
| 58 | File already exists | File creation failed - exists |
| 61 | Disk full | No space on disk |
| 62 | Input past end | READ beyond end of file |
| 63 | Bad record number | Invalid record number |
| 64 | Bad file name | Invalid filename format |
| 67 | Too many files | Maximum files exceeded |
| 68 | Device unavailable | Device not available |
| 69 | Communication buffer overflow | Serial buffer overflow |
| 70 | Permission denied | File access denied |
| 71 | Disk not ready | Drive not ready |
| 72 | Disk media error | Physical disk error |
| 73 | Advanced feature | Feature not available |
| 74 | Rename across disks | Cross-drive rename attempted |
| 75 | Path/File access error | General path error |
| 76 | Path not found | Directory not found |

## B. ASCII Character Codes

### Control Characters (0-31)
| Code | Character | Description |
|------|-----------|-------------|
| 0 | NUL | Null character |
| 7 | BEL | Bell (beep) |
| 8 | BS | Backspace |
| 9 | HT | Horizontal tab |
| 10 | LF | Line feed |
| 13 | CR | Carriage return |
| 26 | SUB | Substitute (Ctrl+Z) |
| 27 | ESC | Escape |

### Printable Characters (32-126)
| Range | Characters |
|-------|------------|
| 32-47 | Space, !"#$%&'()*+,-./ |
| 48-57 | 0123456789 |
| 58-64 | :;<=>?@ |
| 65-90 | ABCDEFGHIJKLMNOPQRSTUVWXYZ |
| 91-96 | [\]^_` |
| 97-122 | abcdefghijklmnopqrstuvwxyz |
| 123-126 | {\|} |

### Extended ASCII (128-255)
Used for special characters, graphics symbols, and international characters depending on the character set.

## C. Color Codes

### CGA Color Palette (SCREEN 1)
| Code | Color |
|------|-------|
| 0 | Black |
| 1 | Blue |
| 2 | Green |
| 3 | Cyan |
| 4 | Red |
| 5 | Magenta |
| 6 | Brown |
| 7 | Light Gray |
| 8 | Dark Gray |
| 9 | Light Blue |
| 10 | Light Green |
| 11 | Light Cyan |
| 12 | Light Red |
| 13 | Light Magenta |
| 14 | Yellow |
| 15 | White |

### Monochrome Attributes
| Code | Attribute |
|------|-----------|
| 0 | Black |
| 1 | Underline |
| 7 | Normal |
| 9 | High intensity underline |
| 15 | High intensity |

## D. Screen Mode Reference

| Mode | Type | Resolution | Colors | Memory |
|------|------|------------|---------|---------|
| 0 | Text | 80×25 or 40×25 | 16 | 4KB |
| 1 | Graphics | 320×200 | 4 | 16KB |
| 2 | Graphics | 640×200 | 2 | 16KB |
| 7 | Graphics | 320×200 | 16 | 64KB (EGA) |
| 8 | Graphics | 640×200 | 16 | 64KB (EGA) |
| 9 | Graphics | 640×350 | 16 | 128KB (EGA) |
| 10 | Graphics | 640×350 | 4 | 128KB (EGA) |

## E. Mathematical Constants

### Commonly Used Constants
```basic
PI# = 3.141592653589793#
E# = 2.718281828459045#
GOLDEN.RATIO# = 1.618033988749895#
SQRT2# = 1.414213562373095#
SQRT3# = 1.732050807568877#
LN10# = 2.302585092994046#
LN2# = 0.693147180559945#
```

### Conversion Factors
```basic
' Angle conversions
DEG.TO.RAD# = 3.141592653589793# / 180#
RAD.TO.DEG# = 180# / 3.141592653589793#

' Temperature conversions
FAHRENHEIT.TO.CELSIUS = (F - 32) * 5 / 9
CELSIUS.TO.FAHRENHEIT = C * 9 / 5 + 32
```

## F. Key Code Reference

### Function Keys (Extended ASCII)
| Key | Code | INKEY$ Result |
|-----|------|---------------|
| F1 | 59 | CHR$(0) + CHR$(59) |
| F2 | 60 | CHR$(0) + CHR$(60) |
| F3 | 61 | CHR$(0) + CHR$(61) |
| F4 | 62 | CHR$(0) + CHR$(62) |
| F5 | 63 | CHR$(0) + CHR$(63) |
| F6 | 64 | CHR$(0) + CHR$(64) |
| F7 | 65 | CHR$(0) + CHR$(65) |
| F8 | 66 | CHR$(0) + CHR$(66) |
| F9 | 67 | CHR$(0) + CHR$(67) |
| F10 | 68 | CHR$(0) + CHR$(68) |

### Arrow and Navigation Keys
| Key | Code | INKEY$ Result |
|-----|------|---------------|
| Home | 71 | CHR$(0) + CHR$(71) |
| Up Arrow | 72 | CHR$(0) + CHR$(72) |
| Page Up | 73 | CHR$(0) + CHR$(73) |
| Left Arrow | 75 | CHR$(0) + CHR$(75) |
| Right Arrow | 77 | CHR$(0) + CHR$(77) |
| End | 79 | CHR$(0) + CHR$(79) |
| Down Arrow | 80 | CHR$(0) + CHR$(80) |
| Page Down | 81 | CHR$(0) + CHR$(81) |
| Insert | 82 | CHR$(0) + CHR$(82) |
| Delete | 83 | CHR$(0) + CHR$(83) |

## G. File Format Information

### .BAS File Structure
GW-BASIC program files use a tokenized format:
- Line numbers stored as 16-bit integers
- Keywords replaced with single-byte tokens
- Numbers stored in internal binary format
- Strings stored as length-prefixed data

### Token Values (Partial List)
| Token | Keyword | Token | Keyword |
|-------|---------|-------|---------|
| 128 | END | 170 | GOTO |
| 129 | FOR | 171 | RUN |
| 130 | NEXT | 172 | IF |
| 131 | DATA | 173 | RESTORE |
| 132 | INPUT | 174 | GOSUB |
| 133 | DIM | 175 | RETURN |
| 134 | READ | 176 | REM |
| 135 | LET | 177 | STOP |
| 136 | GOTO | 178 | PRINT |
| 137 | RUN | 179 | CLEAR |
| 138 | IF | 180 | LIST |
| 139 | RESTORE | 181 | NEW |

## H. Memory Layout

### Typical Memory Organization (64KB System)
```
0000-7FFF: DOS and system memory
8000-8FFF: Program storage (tokenized)
9000-AFFF: Simple variables
B000-CFFF: Array storage
D000-EFFF: String space
F000-FFFF: Stack and system variables
```

### Variable Storage Format
- **Integer**: 2 bytes, two's complement
- **Single-precision**: 4 bytes, Microsoft Binary Format
- **Double-precision**: 8 bytes, Microsoft Binary Format
- **String**: Variable length with descriptor

## I. Graphics Coordinate Systems

### Screen Coordinate Ranges by Mode
| Mode | X Range | Y Range | Origin |
|------|---------|---------|---------|
| 1 | 0-319 | 0-199 | Top-left |
| 2 | 0-639 | 0-199 | Top-left |
| 7 | 0-319 | 0-199 | Top-left |
| 8 | 0-639 | 0-199 | Top-left |
| 9 | 0-639 | 0-349 | Top-left |

### DRAW Command Reference
| Command | Description | Example |
|---------|-------------|---------|
| U | Up | U10 |
| D | Down | D10 |
| L | Left | L10 |
| R | Right | R10 |
| E | Up-right diagonal | E10 |
| F | Down-right diagonal | F10 |
| G | Down-left diagonal | G10 |
| H | Up-left diagonal | H10 |
| M | Move to absolute position | M100,50 |
| B | Blank (move without drawing) | BU10 |
| N | Return to start after draw | NU10 |
| C | Change color | C2 |
| S | Scale factor | S4 |
| A | Angle (0,1,2,3 = 0°,90°,180°,270°) | A1 |

## J. Sound and Music

### PLAY Command Reference
| Command | Description | Range | Example |
|---------|-------------|-------|---------|
| A-G | Notes | | A, B, C, D, E, F, G |
| O | Octave | 0-6 | O4 |
| L | Note length | 1-64 | L4 (quarter note) |
| T | Tempo | 32-255 | T120 |
| P | Pause | 1-64 | P2 |
| > | Octave up | | >C |
| < | Octave down | | <C |
| + | Sharp | | C+ |
| - | Flat | | E- |
| . | Dotted note | | C. |
| ML | Legato | | ML |
| MN | Normal | | MN |
| MS | Staccato | | MS |

### Note Frequencies (Hz)
| Note | Oct 3 | Oct 4 | Oct 5 | Oct 6 |
|------|-------|-------|-------|-------|
| C | 131 | 262 | 523 | 1047 |
| C# | 139 | 277 | 554 | 1109 |
| D | 147 | 294 | 587 | 1175 |
| D# | 156 | 311 | 622 | 1245 |
| E | 165 | 330 | 659 | 1319 |
| F | 175 | 349 | 698 | 1397 |
| F# | 185 | 370 | 740 | 1480 |
| G | 196 | 392 | 784 | 1568 |
| G# | 208 | 415 | 831 | 1661 |
| A | 220 | 440 | 880 | 1760 |
| A# | 233 | 466 | 932 | 1865 |
| B | 247 | 494 | 988 | 1976 |

## K. Useful Subroutines

### String Manipulation
```basic
10000 REM *** STRING UTILITY SUBROUTINES ***
10010 REM
10020 REM TRIM$ - Remove leading and trailing spaces
10030 REM Input: A$ = string to trim
10040 REM Output: A$ = trimmed string
10050 REM
10060 SUB.TRIM:
10070   A$ = LTRIM$(RTRIM$(A$))
10080 RETURN
10090 REM
10100 REM UCASE$ - Convert to uppercase
10110 REM Input: A$ = string to convert
10120 REM Output: A$ = uppercase string
10130 REM
10140 SUB.UCASE:
10150   FOR I = 1 TO LEN(A$)
10160     C = ASC(MID$(A$, I, 1))
10170     IF C >= 97 AND C <= 122 THEN MID$(A$, I, 1) = CHR$(C - 32)
10180   NEXT I
10190 RETURN
```

### File Utilities
```basic
11000 REM *** FILE UTILITY SUBROUTINES ***
11010 REM
11020 REM CHECK.FILE.EXISTS
11030 REM Input: FILENAME$
11040 REM Output: FILE.EXISTS% (0=no, -1=yes)
11050 REM
11060 SUB.FILE.EXISTS:
11070   FILE.EXISTS% = 0
11080   ON ERROR GOTO 11110
11090   OPEN FILENAME$ FOR INPUT AS #15
11100   CLOSE #15: FILE.EXISTS% = -1
11110   ON ERROR GOTO 0
11120 RETURN
```

### Mathematics
```basic
12000 REM *** MATHEMATICAL SUBROUTINES ***
12010 REM
12020 REM FACTORIAL
12030 REM Input: N% = number
12040 REM Output: RESULT# = N! factorial
12050 REM
12060 SUB.FACTORIAL:
12070   RESULT# = 1
12080   FOR I% = 2 TO N%
12090     RESULT# = RESULT# * I%
12100   NEXT I%
12110 RETURN
```

## L. System Configuration

### Memory Requirements
- **Minimum**: 64KB RAM
- **Recommended**: 128KB RAM or more
- **Graphics**: Additional memory for screen buffers
- **Files**: RAM for file buffers

### DOS Configuration
Recommended CONFIG.SYS settings:
```
FILES=20
BUFFERS=15
```

## M. Historical Notes

### Development Timeline
- **1975**: Original Microsoft BASIC for Altair 8800
- **1979**: BASIC-80 for CP/M systems
- **1981**: IBM PC BASIC (BASICA)
- **1983**: GW-BASIC released with MS-DOS
- **1991**: QBasic replaces GW-BASIC in MS-DOS 5.0

### Compatibility Information
GW-BASIC programs are generally compatible with:
- IBM BASICA (with minor differences)
- Microsoft QuickBASIC (with modifications)
- QBasic (subset compatibility)

## N. References and Resources

### Original Documentation
- Microsoft GW-BASIC User's Guide
- Microsoft GW-BASIC Reference Manual
- IBM Personal Computer BASIC Manual

### Source Code Analysis
This documentation is based on analysis of the Microsoft GW-BASIC source code released by Microsoft in 2020, available at:
https://github.com/microsoft/GW-BASIC

### Technical Specifications
- **Processor**: Intel 8086/8088 or compatible
- **Operating System**: MS-DOS 2.0 or later
- **Memory**: Minimum 64KB, maximum 640KB
- **Storage**: Floppy disk or hard disk

## O. Acknowledgments

This documentation was created through careful analysis of the original GW-BASIC interpreter source code. Special recognition goes to:

- **Microsoft Corporation**: For releasing the GW-BASIC source code to the public domain
- **Original Development Team**: Bill Gates, Paul Allen, Monte Davidoff, and the Microsoft BASIC team
- **Assembly Language Analysis**: Study of the original x86 assembly implementation
- **Community Contributors**: BASIC programmers who documented features and techniques over the decades

### Legal Notice
GW-BASIC is a historical software product. The source code is available under the MIT License as released by Microsoft. This documentation is provided for educational and historical purposes.

---

This completes the comprehensive documentation for Microsoft GW-BASIC, covering all aspects from basic programming to advanced system-level features and undocumented capabilities discovered through source code analysis.
