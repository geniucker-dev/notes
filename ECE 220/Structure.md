## Fields in Memory Ordered as in Struct Definition
```C
struct book_t {
 char author[50];
 char title[100];
 uint64_t isbn;
 int32_t pages;
 double price;
 int32_t edition;
 // and any other fields we want
};
```
The sequence of elements in memory:

| author |
| --- |
| title |
| isbn |
| pages |
| price |
| edition |

## Alignment Requirements
Most ISAs (with byte-addressable memory) requires that
- loads and stores of N bytes
- use addresses that are multiples of N.

e.g. 
trying to load a 32-bit value (4B) from address 0x20000001 (= 1 mod 4) causes a program to crash

Compilers must produce working code. Thus compilers align
- fields to their size (for primitive types), 
- and structures to the maximum
alignment needed by any field.

A padding example:
```C
struct one_t {
    int8_t a;
    int32_t b;
}
```
![[assets/structure-1.png]]
A `one_t` must be 4-byte aligned because of `b` **since `b` must be 4-byte aligned**.
After `a`, a compiler:
- inserts 3 bytes of padding
- so that `b` is aligned properly.

What if we change the order?
```C
strict one_t {
    int32_t b;
    int8_t a;
}
```
![[assets/structure-2.png]]
Same result: 8 bytes.
(Arrays of one_ts must have
proper alignment, too.)

## Structure Types Must By Default Include “struct”
By default, the name of a structure type in C **must** include the keyword `struct`.
E.g.
```C
struct book_t a_book, another_book;
```

## Structure Assignment Copies All Bits
```C
struct book_t a_book, another_book;
// … some code to fill in a_book

// What does this assignment do?
another_book = a_book;
```
Copies all bits from `a_book` into `another_book`.
While using a function, to avoid copying the entire structure, we use adddress.
```C
// Why pass a structure’s address?
my_book_printer (&another_book);
```

## Call-by-Value Demands Copies of Structure Arguments
Structures can be large. Hence doing so is rarely acceptable.
> A complex number composed of two floating-point
numbers is an example of a possible exception.

## Example: Define a Stack Structure to Solve a Problem
We'll develop a **stack structure** and some **operations on a stack**
```C
struct stack_t {
 // 500 lines of up to 200 chars
 char data[500][200];
 int32_t top;
};
```
Q: Why only 200 characters per line? And why only 500 lines?
A: Fields must have known size.

However, we can use pointers cuz pointers have known size.


## The `fgets` Function Reads a Line from a Stream
```C
char* fgets (char* s, int size,
             FILE* stream);
```
The fgets function
- reads up to `(size – 1)` characters or until the end of a line (whichever comes first) 
- into array `s` and
- returns `s` on success, or `NULL` on failure.

If we ignore the `stream` argument, we use `stdin` as the default stream, which means we read from the keyboard.

## The `strcpy` Function Copies a String
```C
char* strcpy (char* dest,
              const char* src);
```
`strcpt`
- copies the string from `scr`
- into the array at `dest`
- **The destination must have enough space!** (No checking can be done by the function.)

## Continuing the Stack Example
```C
int main() {
    char buf[200]; // a buffer to store one line
    struct stack_t stack; // declare a stack
    stack.top = 500; // initialize stack to empty

    // read from keyboard until stack full or input ends
    while (0<stack.top && // stack not full
        NULL!=fgets(buf, 200, stdin)) { // input not ended
            strcpy(stack.data[--stack.top], buf); // push (copy from buffer into stack)
        }

    // print a line, pop, and repeat until stack empty
    while (500 > stack.top) {
        printf ("%s", stack.data[stack.top++]);
    }

    return 0;
} // end of main
```
> Important: If the stack is full, no line is requested (`fgets` is not called).

## Data Structures Should Hide Their Implementations
A good data structure
- allows other code to use the structure
- and operations defined on the structure
- without knowing details of the structures’s implementation.

It's called **information hiding**.

## Remember: Pass Pointers, Not Structures
Our structure above is up to 100kB!
So DON'T make a copy.

A Function to Check Whether a stack_t is Empty
```C
// Returns 1 if stack is empty, or
// 0 if stack is not empty.
int32_t stack_empty (const struct stack_t* s) {
    return (500 == (*s).top); // Parentheses required; . has precedence over *
}
```
> Note: The `.` operator has higher precedence than the `*` operator.

## Use the `->` Operator to Access Fields after Dereferencing
`(s->top)` is equivalent to `((*s).top)`.

## A Function to Initialize a stack_t
```C
void stack_init (struct stack_t* s) {
    s->top = 500;
}
```

## A Function to Check Whether a stack_t is Full
```C
// Returns 1 if stack is full, or
// 0 if stack is not full.
int32_t stack_full
 (const struct stack_t* s) {
    return (0 == s->top);
}
```

## Information Hiding and Performance Sometimes at Odds
Caller or callee
- must ensure that string does not disappear after it is pushed,
- but which one? Copying twice is wasteful.

Let’s retain our current design, so `stack_push` must make a copy

## A Function to Push a String Onto a stack_t
```C
int32_t stack_push (struct stack_t* s, const char* str) {
    int32_t i;
    char* write;
    if (stack_full (s)) {
        return 0;
    }
    write = s->data[--s->top];

    // Loop Until End of String or Out of Space
    for (i=0; '\0'!=*str; i++) {
        if (199 == i) { //If str is too long, restore stack top and fail.
            s->top++;
            return 0;
        }
        *write++ = *str++; //Copy a character and advance pointers
    }

    // End the String and Return Success
    *write = '\0'; // write NULL terminator
    return 1; // push succeeded
}
```

## Must Also Copy in `stack_pop`

