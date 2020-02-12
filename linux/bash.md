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
