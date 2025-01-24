# Bash Scripting: Learning Documentation

## Running Commands
- Type `echo hello bash` in the terminal and press **Enter** to run a command directly.
- Commands can also be placed in a file to be executed as a script.

## Creating a shell (`.sh`) Script
1. Use the `touch` command to create a script file:
   ```bash
   touch questionnaire.sh
   ```
2. Open the file in the editor and add the following text:
   ```bash
   echo hello questionnaire
   ```
3. Run the script using the **shell interpreter**:
   ```bash
   sh questionnaire.sh
   ```
4. Run the script using the **bash interpreter**:
   ```bash
   bash questionnaire.sh
   ```

## Using a Shebang
- Locate the bash interpreter path:
  ```bash
  which bash
  ```
- Add a shebang at the top of the file:
  ```bash
  #!/bin/bash
  ```
- Run the script by executing it directly:
  ```bash
  ./questionnaire.sh
  ```

## Handling Permissions
1. List file permissions:
   ```bash
   ls -l
   ```
   Output example: `-rw-r--r--` (no `x` means the file is not executable).
2. Make the file executable:
   ```bash
   chmod +x questionnaire.sh
   ```
3. Verify updated permissions:
   ```bash
   ls -l
   ```
   Output example: `-rwxr-xr-x` (now the file is executable).
4. Run the script:
   ```bash
   ./questionnaire.sh
   ```

## Adding Commands to the Script
- Add commands like `ls -l` to the script to see their outputs:
  ```bash
  echo hello questionnaire
  ls -l
  ```
- Run the script again to view the outputs.

## Introducing Variables
1. Declare a variable:
   ```bash
   QUESTION1="What's your name?"
   ```
2. Use the variable with `$`:
   ```bash
   echo $QUESTION1
   ```
3. Accept user input with `read`:
   ```bash
   read NAME
   ```
4. Combine inputs with echo:
   ```bash
   echo "Hello $NAME."
   ```

## Expanding the Script
1. Add another variable:
   ```bash
   QUESTION2="Where are you from?"
   ```
2. Print the second question and read input:
   ```bash
   echo $QUESTION2
   read LOCATION
   ```
3. Modify the response:
   ```bash
   echo "Hello $NAME from $LOCATION."
   ```

## Adding a Title
- Print a title at the start of the script with empty lines:
  ```bash
  echo -e "\n~~ Questionnaire ~~\n"
  ```

## Adding More Questions
1. Create a third question variable:
   ```bash
   QUESTION3="What's your favorite coding website?"
   ```
2. Print the third question and read input:
   ```bash
   echo $QUESTION3
   read WEBSITE
   ```
3. Modify the final response to include the new input with an empty line at the beginning:
   ```bash
   echo -e "\nHello $NAME from $LOCATION. I learned that your favorite coding website is $WEBSITE!"
   ```

## Countdown Timer Program
1. Create a new script file:
   ```bash
   touch countdown.sh
   ```
2. Give it executable permissions:
   ```bash
   chmod +x countdown.sh
   ```
3. Add a shebang to use the bash interpreter:
   ```bash
   #!/bin/bash
   ```
4. Add a comment to describe the program:
   ```bash
   # Program that counts down to zero from a given argument
   ```
5. Access arguments passed to the script:
   ```bash
   echo $*
   ```
6. Test the script by running it with arguments:
   ```bash
   ./countdown.sh arg1 arg2 arg3
   ```
7. Modify the script to print only the first argument:
   ```bash
   echo $1
   ```
8. Run the script again to verify:
   ```bash
   ./countdown.sh arg1 arg2 arg3
   ```

