# Lab Report 4
Tracking keystrokes in vim and using git commands. Terminal was cleared between each step.

## 1. Log into ieng6.
* Opened terminal.
* `ssh cs15lsp23iy@ieng6.ucsd.edu.`, `<enter>` Local machine was authenticated by private key, so no need to type password.

## 2. Clone your fork of the repository from your Github account.
* `git clone <cmd+v>`, '<enter>' Pasted the github link of the lab7 repository and cloned it into my course account.

## 3. Run the tests, demonstrating that they fail.
* `cd lab7`, `<enter>` Changed working directory to lab7.
* `bash test.sh`, `<enter>` Ran the test and the output shows failures.

## 4. Edit the code file ListExamples.java to fix the failing test (as a reminder, the error in the code is just that index1 is used instead of index2 in the final loop in merge).
* `vim List`, `<tab>`, `<enter>` Opened the file to be fixed in the vim editor. Used `<tab>` to autocomplete the file name.
* `<shift+g>`, `<up>`, `<up>`, `<up>`, `<up>`, `<up>`, `<up>`, Moved to the end of the file and then up to the line with the error.
* `e` Moved to the last character of "index1".
* `r` Replace single character.
* `2` Replaced "1" with "2".
* `:wq`, `<enter>` Saved changes and exited the vim editor.

## 5. Run the tests, demonstrating that they now succeed.
* `bash test.sh`, `<enter>` Ran the test and the output shows no failures.

## 6. Commit and push the resulting change to your Github account.
* `git add List`, `<tab>`, `<enter>` Added the file with changes to the staging area. Used `<tab>` to autocomplete the file name.
* `git commit`, `<enter>, `Fixed by changing last "index1" to "index2"`, `<esc>`, `:wq`, `<enter>` Committed the changes with a comment.
* `git push`, `<enter>` Pushed changes to Github.
