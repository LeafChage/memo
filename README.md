# Memo

Your task stack

## Install
```sh
$
```

## Usage
```sh
memo Your task stack

USAGE:
memo <SUBCOMMAND>

OPTIONS:

SUBCOMMANDS:
all      all your latest task
clear    clear your latest task
help     Print this message or the help of the given subcommand(s)
peek     check your latest task
pop      pop your latest task
push     push your latest task
top      check your latest task
```

## Example
### Push
```sh
memo push "I do something Task1"
memo push "I do something Task2"

memo all
# I do something Task2 (at: 0000000000)
# I do something Task1 (at: 0000000000)

memo push -r "I do something Task3 to first"
memo all
# I do something Task2 (at: 0000000000)
# I do something Task1 (at: 0000000000)
# I do something Task3 to first (at: 0000000000)
```

### POP
```sh
memo all
# I do something Task3 (at: 0000000000)
# I do something Task2 (at: 0000000000)
# I do something Task1 (at: 0000000000)

memo pop
memo all
# I do something Task2 (at: 0000000000)
# I do something Task1 (at: 0000000000)

memo pop -r
memo all
# I do something Task2 (at: 0000000000)
```

### PEEK / TOP and ALL
```sh
memo all
# I do something Task3 (at: 0000000000)
# I do something Task2 (at: 0000000000)
# I do something Task1 (at: 0000000000)

memo all -n 1
# I do something Task3 (at: 0000000000)

memo all -r -n 2
# I do something Task1 (at: 0000000000)
# I do something Task2 (at: 0000000000)

memo peek # memol top
# I do something Task3 (at: 0000000000)

memo peek -r # memol top -r
# I do something Task1 (at: 0000000000)
```

## Recommend
Customize your shell

```sh
###
### for example
###

PS1_TASK=""
task() {
    memo peek | sed "s/ (at [0-9]*)//g"
}
PS1_TASK='$(task)'

export PS1="$PS1_TASK\n >"
```

