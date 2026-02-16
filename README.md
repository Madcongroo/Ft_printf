# ft_printf (42)

A custom reimplementation of the standard C `printf()` function.

This project builds a static library, `libftprintf.a`, that you can link into your own programs.

## What’s inside

- `ft_printf()` implementation with format parsing
- Helpers to print characters/strings/numbers to standard output
- Conversions implemented:
	- `%c` character
	- `%s` string (prints `(null)` for `NULL`)
	- `%p` pointer address (prints `0x` + lowercase hex)
	- `%d` / `%i` signed integer
	- `%u` unsigned integer
	- `%x` / `%X` hexadecimal (lower/upper)
	- `%%` literal percent sign

## Project files

- `ft_printf.c`: main parsing loop + dispatcher
- `ft_printf_firstcall.c`: pointer/hex/unsigned/signed printing entry points
- `ft_printf_utils.c`: small utilities (`ft_itoa`, `ft_strdup`, helpers for hex)
- `ft_printf_smallfunc.c`: small I/O helpers (`ft_putchar`, `ft_putstr`, ...)
- `ft_printf.h`: public prototypes

## Build

Compile the static library:

```bash
make
```

Cleaning targets:

```bash
make clean   # removes .o
make fclean  # removes .o and libftprintf.a
make re      # rebuild everything
```

Output:

- `libftprintf.a`

## How to use

1) Include the header in your code:

```c
#include "ft_printf.h"
```

2) Compile and link with the library:

```bash
cc -Wall -Wextra -Werror main.c libftprintf.a -o demo
./demo
```

Or using the `-l` form:

```bash
cc -Wall -Wextra -Werror main.c -L. -lftprintf -o demo
```

## Notes / limitations

- This is not a full `printf()` clone: no flags, width, precision, or floating-point conversions.
- Output is written to standard output using `write(1, ...)`.

## What I learned

- Variadic functions in C (`va_list`, `va_start`, `va_arg`, `va_end`)
- Building a format parser and dispatching conversions
- Converting numbers to strings (decimal/hex) and handling edge cases
- Managing memory correctly in utility functions
- Creating and using a static library (`ar rcs`, Makefile targets)