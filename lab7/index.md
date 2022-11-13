
# Part 1

I choose the task **Changing the name of the start parameter and its uses to base**

**process**:

`vim<space>Doc<tab><enter>`

- Open the file *DocSearchServer.java* in vim
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/1.png)

`/start<enter>`

- In this step, I search the word start in normal mode. After I click <enter>, the cursor locate in the firt letter of the firt word *start* it found. 
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/2.png)

`ce`
- `c` means change, then `e` made the cursor move to the end of the word where it located, and delete the whole word. In this example, cursor moved to the end of the word *start* and delete the word *start*. Then the vim start the *insert mode*.
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/3.png)

`base<esc>`
- In insert mode, I typed word *base* in the location where *start* used to be. Then I click `esc` to leave the insert mode, back to normal mode.
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/4.png)

`n`
- `n` let vim keep search the next word *start*, and move cursor to the first letter of it.
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/5.png)

`.`
- `.` means repeat what I did, in this case, it repeat the command `cebase<esc>`, which changed this word *start* to *base*.
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/6.png)

`n.`
- Then I used `n.` again, to change the last word *start* in getfile method.
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/7.png)

`:wq`
- After finish edit, save the file and leave. 
![](https://ruili4ucsd.github.io/cse15l-lab-reports/lab7/8.png)


# Part 2

**Time**
- local: 91 seconds.
- remote in vim: 123 seconds.


**Trouble**
- At first, I wanted to run vim remotely with ssh for editing, but this time I got some indescribable errors, which I guess is because the default windows PowerShell does not support the vim editor. Therefore, I chose to use scp to remotely transfer the file, modify it locally, and then remotely transfer it to the ieng6 server to run the test.

**Question**
- Which of these two styles would you prefer using if you had to work on a program that you were running remotely, and why?

    If many places need to be modified in the file, and it is not very dependent on the running environment, then I tend to modify it locally. Because I am more familiar with the interface of VS code on Windows, windows also provide a lot of shortcut keys for me to make quick and intuitive edit. Vim is undoubtedly a powerful piece of software, but the sheer number of commands and different mode settings can easily make me dizzy. Maybe it will improve when I get familiar with Vim in the future.

- What about the project or task might factor into your decision one way or another? (If nothing would affect your decision, say so and why!)

    In some specific cases, I will only be able to modify in the remote terminal. For example, my project files are all written in C language, and my local terminal does not support C language compiling and running, so I have to modify and test in the remote terminal.
     Alternatively, if the project file is so large that it takes a lot of time to transfer, I also have to make changes remotely.
     Or, if the project file is not allowed to be copied, so I can only modify it in the remote terminal.
     Or, if the project file can only be run in a Linux environment, and the project file depends on a specific configuration file on the remote terminal...
     There are various situations, and I have to learn to be flexible.













