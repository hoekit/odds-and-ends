# Assembly Code

A collection of articles, videos and information related to coding in assembly.


----

x86_64 Linux Assembly #1 - "Hello, World!"
    - https://www.youtube.com/watch?v=VQAKkuLL31g

x86_64 Linux Assembly #2 - "Hello, World!" Breakdown
    - https://www.youtube.com/watch?v=BWRR3Hecjao

x86 Assembly Language Programming
    - https://cs.lmu.edu/~ray/notes/x86assembly/
    - Examples in Linux, macOS and Win32

x86-64 Assembly Language Programming with Ubuntu (pdf)
    - http://www.egr.unlv.edu/~ed/assembly64.pdf
    - Uses yasm (see below)
    - Textbook/reference style rather than tutorial style

Programming in Assembly with Linux
    - https://umlabs.wordpress.com/2011/10/29/programming-in-assembly-with-linux/

The Best and Worst GCC Compiler Flags for Embedded
    - https://interrupt.memfault.com/blog/best-and-worst-gcc-clang-compiler-flags
    - Reading this to find ways to make executables smaller

The 101 of ELF files on Linux: Understanding and Analysis
    - https://linux-audit.com/elf-binaries-on-linux-understanding-and-analysis/
    - Useful to understand how binaries in Linux are organized

A Linux Assembly Language Programming book on oreilly.com
    - https://www.oreilly.com/library/view/linux-assembly-language/0130879401/

Yasm - A complete rewrite of the NASM assembler
    - http://yasm.tortall.net/

----

Tutorial

- File: hello.asm

```
section .data
        text db "Hello, World!",10

section .text
        global _start

_start:
        mov rax, 1
        mov rdi, 1
        mov rsi, text
        mov rdx, 14
        syscall

        mov rax, 60
        mov rdi, 0
        syscall

```

- Build, link and run executable
```
    nasm -f elf64 -o hello.o hello.asm
    ld -o hello hello.o
    ./hello
```
