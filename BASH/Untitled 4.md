



until [ <some test> ]  
do  
<commands>  
done







## Example : 



#!/bin/bash

# Basic until loop

counter=1

until [ $counter -gt 10 ]

do

  echo $counter

  ((counter++))

done





