# learnyoubash

Get more info on commands:
man pwd - gets the manual
pwd --help - most commoads have a help flag

HELLO WORLD
------------

Notes from learnyoubash from node school

Create files with .bash extension

Place the <shebang> at the top:  #!/usr/bin/env bash

Make a file executable:

chmod +x hi.bash

simple example ./hi.bash (in the file)

run via:   ./hi.bash  (i.e. ./<fileName> when in root directory)



VARIABLES
----------

No data types, variables can contain only numbers or a string of one or more chars.

Local variables: exist only within a single script. 
- Declared via = witn no spaces (e.g. foo="value")
- Retrieved using $ (e.g. echo $foo)
- Can be deleted using unset (e.g. unset foo)
- Can be used in strings with "", not in strings with ''

Environment variables:
export GLOBAL_VAR="I am a variable"
e.g. $PATH, $PWD, $RANDOM


POSITIONAL PARAMETERS
_____________________

Variables that are passed in after the file name (like node)

e.g. ./script.sh foo bar
$0 -> Script name
$1 ... $9 -> parameters 1-9
${10} ... ${N} -> p 10-N
$* or $@ -> All positional parameters except $0
$FUNCNAME -> The function name, only has a value inside the function

Default variables:
# Assign FOO value 'default' if it's empty
FOO=${FOO:-'default'}


ARRAYS
-------

IFS -> environment variable that means input field separator by default it is IFS=' '

declaration
Create arrays by assigning values to positions
e.g.
fruits[0]=Apple
fruits[1]=Pear
fruits[2]=Plum
echo ${fruits[@]} or echo ${fruits[*]}

can also be assigned via
fruits=(Apple Pear Plum)

slice operator:
echo ${fruits[*]:0:2}  # Apple Pear // returns a slice of length 2 that starts at 0

Compound assignments:
fruits=(Orange ${fruits[*]} Banana Cherry) // adds in entire existing fruits array

Deleting from arrays
unset fruits[0]

slicing with input params

words=(I am "${@:2:2}" and "${@4:1}")


SHELL EXPANSIONS
----------------

Expansions are a mechanism to calculate arithmetical operatins, to save results of command's executions and so on

Brace expansion:
Allow us to generate arbitrary strings, similar to file expansion

e.g.  echo beg{i,a,u}n  # begin began begun
      spaces are not allowed

Also can be used to generate ranges:

e.g.  echo {0..5}  # 0 1 2 3 4 5
      echo {00..8..2}  # 00 02 04 06 08

Command substitution:
Allows us to evaluate a command and substitute its value into another command or variable assignment 
- performend when a command is enclosed by `` or ${}

e.g.  now=`date +%`  or now=${date +%}

echo $now  #  19:08:26


Arithmetic expansion:
Must be in $(( ))

e.g.  result=$(( ((10 + 5*3) - 7) / 2 ))
      echo $result  #9




