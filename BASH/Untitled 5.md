




while [ <some test> ]  
  do  
  <commands>  
  done




## Example : 



#!/bin/bash

# Basic while loop

counter=1

while [ $counter -le 10 ]

  do

  echo $counter ((counter++))

  done

echo All done

