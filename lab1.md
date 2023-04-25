# Lab Report 1

## Installing VS Code for Mac
  1. [Go to the website for download options.](https://code.visualstudio.com/download)
  2. Download the version for Mac.
  3. Open Finder
  4. Move the downloaded file to the Applications folder. ![Image](Images/move.png)
  5. Open VS Code.
  6. Open a new terminal using the top menu bar. ![Image](Images/menu.png)
  ![Image](Images/terminal.png)

## Remotely Connecting
  1. [Look up your course account.](https://sdacs.ucsd.edu/~icc/index.php)
  2. Fill out the Account Lookup with your student username and ID. Your username is whatever is front of @ucsd.edu in your UCSD email.
  3. Click on the button that says "cs15lsp23XX". This is your course account username. Write it down somewhere because you will need it to login. ![Image](Images/accounts.png)
  4. Proceed to the password change tool to set your password. Make sure to enter your course account username and not your student username. ![Image](Images/tool.png)
  6. Now you are ready to remotely access the ucsd servers. Type the following command into the VS Code terminal, replacing username with your username.
  ```
  ssh username@ieng6.ucsd.edu
  ```
  4. Enter your password. The terminal will stay empty, so type it out completely then return.
  ![Image](Images/login.png)

## Trying Some Commands
  Use the following commands to create, move, and delete files.
  * `pwd`: Print the folder you are in.
  * `ls`: List folders and files inside the current folder.
  * `mkdir hello`: Makes a new folder called hello.
  * `cd hello`: Moves into the folder called hello.
  * `cd ..`: Moves one level out of the current folder.
  * `rmdir hello`: Deletes the folder called hello.
  * `cat`: Reads contents from a file. [Read the documentation.](https://www.geeksforgeeks.org/cat-command-in-linux-with-examples/)
  * `mv`: Moves files. [Read the documentation.](https://www.geeksforgeeks.org/mv-command-linux-examples/)
  * `cp`: Copies files. [Read the documentation.](https://www.geeksforgeeks.org/cp-command-linux-examples/)
  
  Here are some examples of running commands.
  ![Image](Images/example1.png)
  1. `pwd` tells us that the filepath of the current folder is "/home/linux/ieng6/cs15lsp23/cs15lsp23iy".
  2. `ls` shows us that the current folder contains "perl5" and "wavelet".
  3. `mkdir hello` creates a new folder called "hello".
  4. `ls` visually confirms that the folder has been created.
  5. `cd hello` changes the working directory to the newly created folder "hello".
  6. `ls` generates no output because this folder is empty.
  7. `cd ..` moves out of the folder "hello". We are back to where we were in the beginning.
  8. `rmdir hello` deletes the "hello" folder. This only works if the folder is empty. `rm -r hello` is required to delete a folder along with everything inside of it. 
  9. `ls` shows us that the "hello" folder is now gone.
  
  ![Image](Images/example1.png)
  1. `mkdir hello` creates a new folder called "hello".
  2. `cd hello` moves into the new folder.
  3. `cat > hello.txt  creates a new txt file and allows us to write stuff in it. I typed "hello there," hit return, then closed the file with control-c. 
