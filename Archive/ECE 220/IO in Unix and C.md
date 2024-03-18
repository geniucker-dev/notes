Unix (and C) supports
- a **unified** notion of I/O
- known as **file descriptors**

Programs can use file descriptors to
- read from the keyboard,
- write to the display (virtual or physical),
- read and write files,
- communicate with devices (such as printers),
- communicate over network connections, and
- communicate with other programs.

## Programs Can Be Oblivious to “Type” of File Descriptor

## File Descriptors are Small Integers
Access to any device is usually a privileged operation.
OS maintains information
- about each I/O channel
- For a given program,
- the information is kept **in an array**.

Then a **file descriptor** is just an **index** into the array.

## Buffering
### Most I/O in C Uses Streams
**Streams** provide
- a continuous sequence of bytes
- typically including some kind of **buffering**.

## Buffering Happens for Both Reading and Writing
Buffering means:
- **waiting until** a certain amount or type of
data is available before sending anything
- **reading extra data** in anticipation of
future requests for data

## OS and Stream Both Buffer on Reads
E.g. When a program requests 1B, the OS may read 4KB and store the rest in a buffer (since data on disk come in maybe 4KB blocks, and a system call is too expensive just to read 1B).

## A C Stream is a `FILE*`
Where does buffering happen with a stream in C?
Of course, in a data structure.

A **Stream in C** is
- a pointer to that structure
- with type `FILE*`

P.S. The structure itself is not usually used. But you can see by compiling with `-E` to see the preprocessed code.

## Three Streams by Default, but Can Create More
A C program has three default streams:
- stdin (descriptor 0) keyboard
- stdout (descriptor 1) display(normal)
- stderr (descriptor 2) display(error)

You can create other stream variables
```C
FILE* my_file;
```

## Descriptors Can Be Overridden When a Program Starts
E.g. You can save normal output to a file and deliver error output to the display.

## Open a File on Disk as a Stream Using `fopen`
```C
FILE *fopen(const char* path,
             const char* mode);
```
- `path`: The path to the file
- `mode`: Specifies how the file will be used
  - `"r"` or `"rb"`: read only
  - `"w"` or `"wb"`: write only (after truncation)
  - `"a"` or `"ab"`: append (write only, at end)
  - `"r+"` or `"rb+"` or `"r+b"`: open r/w (read/write)
  - `"w+"` or `"wb+"` or `"w+b"`: truncate and open r/w
  - `"a+"` or `"ab+"` or `"a+b"`: append r/w
- return: a **new stream** on sucess, `NULL` on failure

## Close a Stream Using `fclose`
```C
int fclose(FILE* stream);
```
- `stream`: the stream to close
- return: `0` on success, `EOF` (`-1`) on failure

**DO NOT** leave streams unclosed.

## Use `fgetc` or `getc` to Read a Character from a Stream
```C
int fgetc(FILE* stream);
int getc(FILE* stream);
```
- `fgetc` is a library function
- `getc` is a macro

Both return one byte or `EOF`.

## Use `fputc` or `putc` to Write a Character to a Stream
```C
int fputc(int c, FILE* stream);
int putc(int c, FILE* stream);
```
Similarly,
- `fputc` is a library function
- `putc` is a macro

Character to write passed as an int (native integer) for speed.
**Returns** character written (zero-extended from low 8 bits of c) or EOF on failure.

## Use `getchar`/`putchar` as Shortcuts with `stdin`/`stdout`
for reading
```C
int getchar(void);
```
for writing
```C
int putchar(int c);
```

## Use `fgets` to Read a String from a Stream
```C
char* fgets(char* s, int size,
             FILE* stream);
```
- `s`: where to store the string
- `size`: usually size of the array
- `stream`: the stream to read from
- return: `s` on success, `NULL` on failure

**`fgets` also stops reading at End of Line**
`fgets` stops at the first of the following 3 conditions:
- **end of the input** (such as a file)
- **end of a line** (ASCII 0x0A or 0x0D)
- **end of array `s`** (leaving room for a `NUL`

`fgets` is the best way to process line-oriented inputs.

## Use `fputs` to Write a String to a Stream
```C
int fputs(const char* s,
           FILE *stream);
```
- `s`: the string to write
- `stream`: the stream to write to
- return: non-negative on success, `EOF` on failure

## `puts` Writes to stdout with an End of Line Sequence
```C
int puts(const char* s);
```
`puts` adds an end of line sequence to the end of the string (while `fputs` does not).

**DO not EVER use shortcut for reading a string from `stdin`. It is a security hazard.**

## `fprintf` and `fscanf`
```C
fprintf(FILE* stream, const char* format, ...);
fscanf(FILE* stream, const char* format, ...);
```

## `fread` and `fwrite` for Binary I/O
```C
size_t fread(void* ptr,
             size_t size, size_t n_elt,
             FILE* stream);
```
- `ptr`: address to which data are stored
- `size`: size of one "thing"
- `n_elt`: number of "things"
- `stream`: the stream to read from
- return: number of "things" read or 0 on failure


## Use `fgets` & String “I/O” to Parse Human-Readable Files

## `sscanf` to Read Formatted Input from a String
```C
int sscanf(const char* s, const char* format, ...);
```

## `snprintf` to Write Formatted Output to a String
```C
int snprintf(char* s, size_t size,
             const char* format, ...);
```
return: returns number of characters printed or negative number on failure

## System Calls Provide a Reason for Failure in `errno`
When system calls (or functions that call system calls, such as `fopen`) fail, they set a (thread-specific) variable called `errno` to an error number indicating the reason.  
Code can check error numbers: for example, `ENOENT` means that the file does not exist.

## Use `perror` to Print a Human-Readable Error Message
To print a human-readable error message to stderr, use `perror`:
```C
void perror(const char* prefix);
```
The prefix, a colon, and a space are printed before the error message, and a newline is printed after the error message.

