# Bash Scripting

> **Resources Used:**  
`/Users/paul/Documents/Personal Projects/bash_script_test` - directory i’m working in  
[Bash Reference Manual](http://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash#Introduction)  
[Utilizing this YouTube playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IKioClkSNDjW7iz-6TFvLwS)  
[How to set your $PATH variable in Linux](https://opensource.com/article/17/6/set-path-linux)  
[Top 25 Commands and Creating Custom Commands](https://www.educative.io/blog/bash-shell-command-cheat-sheet)  
[vi[m] Cheatsheet](http://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf)  
[How to Create Bash Aliases](https://linuxize.com/post/how-to-create-bash-aliases/)
> 

---

# How do we know we’re in the Bash Shell?

```jsx
which $SHELL

output:
/bin/bash
```

# What is creating a bash script mean?

- Put simply, it’s just automating what we write in the command line. We run a script to have it run a sequence of CL commands.

# Writing a script

## Starting a new script

- In the terminal, write . . .

```jsx
nano *name_of_script*.sh
```

## Getting the CL to know that we are writing a bash script

- Write this as the first line of the script . . .
    - We’re telling the bash interpreter what scripting language we want to use for the script that we are writing . . .

```jsx
#!/bin/bash
```

## Addition, multiplication, and division

```jsx
expr 2 + 2

**output:** 4
```

## Allowing user-input in the script

```jsx
#!/bin/bash

echo "type your name..."
read name
echo "hi, $name!"
```

## Allowing arguments to be passed into the bash script

```jsx
./<script-name>.sh paul 21

// $1=paul
// $2=21
//so we could do something like . . . 

echo hello $1, you are $2 years old.
```

## Using CL commands to set variables

```jsx
#!/bin/bash
user=$(whoami)

echo "you are logged in as $user"
```

## RANDOM, PWD, HOSTNAME,

```jsx
echo $RANDOM // will echo a random number from 0-32767

echo $PWD // prints current path

echo $HOSTNAME // name of host (should be local)
```

## Exporting variables

- You are able to declare variables of your own in the CL
    
    ```jsx
    twitter="tweet tweet"
    ```
    
- Once you have that, you are able to export that variable
    - This allows us to use twitter **in a script**
    
    ```jsx
    export twitter
    ```
    

## Editing the .bashrc Script / Making a Variable Permanent

- In order to **make a variable permanent and remain even after a session closes, we have to use the `.bashrc`**
    
    ```jsx
    // inside of .bashrc script
    export twitter="tweet tweet" 
    ```
    
    - Now just either log out of the session and rerun as **.bashrc will be ran at the start of every session** OR do **`source .bashrc`**

# Running a Script

```jsx
bash <script_name>
```

## Making a Script Executable

```jsx
chmod +x <script_name>
```

# What is a PATH, how do you set it up and why would you do it?

- PATH = An **environment variable** that stores **multiple directories** so that **you don’t have to specify the location of some program.**
- Example: say that I wrote a script called [hello-world.sh](http://hello-world.sh) and it’s in a directory called `/place/with/the/file`
    - This file provides some useful function to all the files in my current directory, that I **want to be able to execute no matter what current directory I’m in.**
    - We can simply **add** `/place/with/the/file` to the `$PATH` variable with the following command
    
    ```jsx
    export PATH=$PATH:/place/with/the/file
    ```
    
    - This allows us to be able to execute the script anywhere on my system by just typing in its name, without having the specify the full path to it.
- If I want to be able to permanently add a directory path to the global $PATH variable, I can edit the `.bashrc` or any of the other scripts that are executed at the start of a bash session.

# Creating Alias

## Why create an alias?

- They allow you to write a shortcut of a longer command.
    
    ```jsx
    // Example:
    // instead of typing:
    youtube-dl -x —audio-format mp3 [link]
    
    // i can create an alias for -x --audio-format mp3 so i don't have to type it out everytime
    // in ~/.bashrc file
    alias mp3="-x —audio-format mp3"
    // allowing me to write this instead of the above
    youtube-dl mp3 [link]
    ```
    

### General format of creating an alias

```jsx
alias *alias_name*="*command to run*"
```

## Creating bash aliases with arguments (bash functions)

### General format of bash function

```jsx
function_name() {
    [commands]
}
or
function function_name {
    [commands]
}
```

## Example: Create a bash function that creates a directory and cd’s to it

```jsx
mkcd()
{
    mkdir -p -- "$1" && cd -P -- "$1"
}

Utilizing it . . .
mkcd new_directory
```

---

- `--` - makes sure you’re not accidentally passing an extra argument to the  command. For example, if you try to create a directory that starts with `-` (dash) without using `--` the directory name will be interpreted as a command argument.
- `&&` - ensures that the second command runs only if the first command is successful.
- Reference **[Run multiple commands in one line with `;`, `&&` and `||` - Linux Tips](https://dev.to/0xbf/run-multiple-commands-in-one-line-with-and-linux-tips-5hgm)**

## Listing all aliases

```jsx
> alias
```

## Unaliasing made aliases

```jsx
unalias <alias-name>

unalias -a // unaliases all aliases
```