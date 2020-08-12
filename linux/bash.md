# Bash

## Arrays

### Create

The `+=` operator can be used to append or add values

```bash
 ARRAY=()
 ARRAY+=('foo')
 ARRAY+=('bar')
 ```

### Access
* by index `${myarray[0]}`
* all array elements using `${myarray[@]}` 
 
### String into array
 
#### Using tr command
 ```bash
  new_array=($(echo $a_string | tr ";" "\n"))
 ```

#### Using IFS

```bash
IFS=';' read -ra my_array <<< "$my_string"
```

### Traverse an array
 
```bash
  for i in "${an_array[@]}"
  do
    echo $i 
  done
```

### Use as function argument

To pass one or more arguments AND an array, the array should be the last argument and only one array can be passed.

```bash
function func() {
   local at1="$1"   # Save first argument in a variable
   shift            # Shift all arguments to the left (original $1 gets lost)
   local arr=("$@") # Rebuild the array with rest of arguments
   
   #...
}
```

## Conditionally pass params to a script

The most expansible and robust way would probably be to use an array to hold the optional parameter(s):

params=()
if [[ $CONDITION == true ]]; then
    params+=(--param2)
fi
script param1 "${params[@]}"
Or in shorthand:

[[ $CONDITION == true ]] && params+=(--param2)
script param1 "${params[@]}"
That avoids repeating the constant part of the command and you can put more than one argument in the array, even the whole command.

Note that it's important to do this with an array: if you replace the array with a regular variable (params="--param2"; script param1 $params) you'll either have to expand the variable unquoted, with all the problems that brings, or expand it quoted, in which case you'll pass an empty string as argument if the variable is empty.

In a simple case like this, the "alternate value" expansion can also be used:

cond=x
p2="--param2"
script param1 ${cond:+"$p2"}
Here, if cond is nonempty (regardless of if it's cond=false or cond=0 instead of cond=true), the value of p2 is expanded. This may be seen as less ugly than arrays, but be careful with the placement of the quotes.

See also:

* https://unix.stackexchange.com/q/444946/170373
* https://unix.stackexchange.com/q/459367/170373
* https://unix.stackexchange.com/q/131766/170373