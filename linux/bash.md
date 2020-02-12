### Bash

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
