




# A simple menu

select var in <list>  
do  
<commands>  
done





## Example : 


#!/bin/bash

options=‘Run Load Save Quit'

PS3='Select an action: '

select option in $options

do

  if [ $option == 'Quit’ ]

  then

       break

  fi

  echo You Chose $option

done



>[!warning]
>
>
>## Exceptions : 
>
>1.Enter Key only: Display menu again
>
>2.Any choice not in the list: Option will be null





