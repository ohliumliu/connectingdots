## Strinification in C macro
`#define m1(x) "literal " #x`
```c
foo = 4
m1(foo) //this is a string "literal foo"
```
I guess ruby and python inherited this.

## Concatenation in C macro
`# define paste(a, b) a ## b`
```c
paste(a, b) // this is a string "ab"
```
