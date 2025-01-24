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


## Countdown Timer Script

1. **Creating the Script**:

   - Create the file: `touch countdown.sh`.
   - Add execute permissions: `chmod +x countdown.sh`.
   - Add a shebang: `#!/bin/bash`.
   - Comment: `# Program that counts down to zero from a given argument.`

2. **Using Arguments**:

   - Print arguments: `echo $*`.
   - Access specific arguments: `echo $1`.

3. **Conditions**:

   - Use `if` syntax:
     ```bash
     if [[ CONDITION ]]
     then
       STATEMENTS
     fi
     ```
   - Example: `if [[ $1 -gt 0 ]]; then echo "Positive integer."; fi`.
   - Add `else`:
     ```bash
     if [[ $1 -gt 0 ]]
     then
       echo "Positive integer."
     else
       echo "Include a positive integer as the first argument."
     fi
     ```

4. **Expressions and Operators**:

   - Arithmetic: `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`.
   - String: `==`, `!=`.
   - File: `-a` (exists), `-x` (executable).
   - Logical: `&&` (and), `||` (or).

   Example:

   ```bash
   if [[ -x countdown.sh && $1 -gt 0 ]]
   then
     echo "Valid file and argument."
   fi
   ```

5. **Loops**:

   - `for` syntax:
     ```bash
     for (( i = START; i >= END; i-- ))
     do
       echo $i
     done
     ```
   - Add a loop to count down from the argument:
     ```bash
     if [[ $1 -gt 0 ]]
     then
       for (( i = $1; i >= 0; i-- ))
       do
         echo $i
       done
     else
       echo "Include a positive integer as the first argument."
     fi
     ```

6. **Testing for Positive Integers**:

   - Check if the argument is a positive integer:
     ```bash
     if [[ $1 =~ ^[0-9]+$ && $1 -gt 0 ]]
     then
       echo "Valid positive integer."
     else
       echo "Provide a positive integer as an argument."
     fi
     ```

---

### Additional Explorations

1. **Testing Exit Status**:

   - Commands have exit statuses:
     - `0`: Success.
     - Non-zero: Error.
   - View exit status: `echo $?`.

   Examples:
   ```bash
   [[ 4 -le 5 ]]; echo $?   # 0 (true)
   [[ 4 -ge 5 ]]; echo $?   # 1 (false)
   ```

2. **Combining Expressions**:

   - Use `&&` (and) or `||` (or):
     ```bash
     [[ -x countdown.sh && 5 -le 4 ]]; echo $?  # 1 (false)
     [[ -x countdown.sh || 5 -le 4 ]]; echo $?  # 0 (true)
     ```

3. **Testing Files**:

   - Check if a file exists: `[[ -a countdown.sh ]]; echo $?`.
   - Check if a file is executable: `[[ -x countdown.sh ]]; echo $?`.

4. **Testing Multiple Conditions**:

   - Use `&&` to combine tests:
     ```bash
     [[ -x countdown.sh && -a questionnaire.sh ]]; echo $?
     ```

5. **Using Expressions in Loops**:

   - Example:
     ```bash
     for (( i = 10; i > 0; i-- ))
     do
       [[ $i -eq 5 ]] && echo "Halfway there!"
       echo $i
     done
     ```
