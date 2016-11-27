#### IMPORTANT NOTES ABOUT BASH

## File set-up

First line of the file should contain `#!/usr/bin/env bash`. This tells the system
what program to use (in this case, Bash).

To make a file executable, change its read/write values..

```bash
chmod +x file.sh
```

## Variables

Only two data types (or more appropriately, zero data types) -- Strings and Numbers

- To declare a variables, use `=` with _no spaces_.
- To display a variable, use the `echo` command.
- To delete a variable, use the `unset` command.

```bash
foo="Andy"
echo $foo       # > Andy
unset foo       # deleted
```

## Single Quotes vs. Double Quotes

- Variables contained within double quotes will be expanded / evaluated.
- This is not the case with single quoted strings.

```bash
NAME="Denys"
echo "My name is $NAME"   # > My name is Denys
echo 'My name is $NAME'   # > My name is $NAME
```

## Environmental Variable

To expose a variable beyond the file scope, declare its value with `export`.

```bash
export MY_GLOBAL="see/me/from/anywhere"
```

note: There are _a lot_ of [global variables in bash](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_02.html#sect_03_02_04).
You will meet these variables fairly often, so here is a quick lookup table with
the most practical ones:

| Variable | Description                                                                  |
|:---------|:-----------------------------------------------------------------------------|
| $HOME    | The current user's home directory.                                           |
| $USER    | The current user.                                                            |
| $PATH    | A colon-separated list of directories in which the shell looks for commands. |
| $PWD     | The current working directory.                                               |
| $RANDOM  | Random integer between 0 and 32767.                                          |
| $UID     | The numeric, real user ID of the current user.                               |
| $PS1     | The primary prompt string.                                                   |
| $PS2     | The secondary prompt string.                                                 |


## Positional Parameters

Allocated when the function is evaluated. Here's a list:

| Parameter    | Description                                             |
|:-------------|:--------------------------------------------------------|
| $0           | Script's Name                                           |
| $1 … $9      | The parameter list elements from 1 to 9.                |
| ${10} … ${N} | The parameter list elements from 10 to N.               |
| $* or $@     | All positional parameters except $0.                    |
| $#           | The number of parameters, not counting $0.              |
| $FUNCNAME    | The function name (has a value only inside a function). |

In this example, `./script.sh foo bar`
```bash
# the parameter values would be...

# $0='./script.sh'
# $1='foo'
# $2='bar'
```

## Default parameter values

Variables/parameters can have default values defined with `{VAL:-'defaultValue'}` syntax.

```bash
# Assign FOO value 'default' if it's empty
FOO=${FOO:-'default'}
```
