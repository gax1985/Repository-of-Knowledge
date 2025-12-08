



# READ Statement 




## Definition :



> The Bash **`read`** command is a built-in utility that reads text from standard input. The tool offers many functionalities for reading user input, helping make [Bash scripts](https://phoenixnap.com/kb/write-bash-script) interactive.




## Uses of the READ Statement in BASH : 



Store typed data into a *variable* :


		read <VARIABLE>


Store typed information into an *array* of your choice : 


		read -a <ARRAY>



Specify the *maximum number of characters allowed to be stored in a* **VARIABLE** :


		read -n <NUMBEROFCHARACTERS> <VARIABLE>


Specify the *delimiter* in use when typing multiple items : 


		read -d "," <VARIABLENAME>


Display a **Prompt** before storing the user's *input* : 


		read -p "Please enter your question : " <VARIABLENAME>



Do **NOT** *display the entered text* :


		read -p -s "Please enter your clandestine question : " <VARIABLENAME>


Do a **Time-Out** after a *number of seconds* : 


		read -t <numberofseconds> <VARIABLENAME>





