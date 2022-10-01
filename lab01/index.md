# CSE 15L FALL 2022 LAB01



***Student Name: Rui Li***

***Student User Name: cs15lfa22fc***



### ***This is only for Windows10 OS***



## Installing VScode



Go Google to find VS Code, and install it. 

After install successful, you can open it and you should see something like this:



![Installing VScode](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/Installing_VScode.png) 



## Remotely Connecting



Go to https://sdacs.ucsd.edu/~icc/index.php, find your username and password for CSE15L, and reset your password. 

After you find your password, you can open VS Code and press "ctrl" + "\`" to run a powershell. 

Then, run the following code in powershell:

`ssh YourUserName@ieng6.ucsd.edu`

The powershell will ask you to enter your password. You won't see your password in screen.

If the password is wrong, the powershell will ask you to enter it again.

If you successful, you will see something like this:



![log in](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/log_in.png)



## Trying Some Commands



Next, let's try some command in remote station.

Try to type the following command, and you should got some ouptput very familiar with the screenshot.



![run some command](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/Run_Some_Command.png)



## Moving Files with scp



Now we gonna use scp to copy the file from your local station to the remote station. 

Use `exit` to log out from remote station.

Create a file called WhereAmI.java in your local station users folder. It should contain code:



    class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
       }
    }



Next, run command below in your powershell：

`javac WhereAmI.java`

`java WhereAmI`



This should print the Operating System, your user name, and your working pasth in your powershell. 



Next, use scp to transfer file to remote station:

`scp WhereAmI.java YourUserName@ieng6.ucsd.edu:~/`



This should send the WhereAmI.java to remote station.



Then log in to your ieng6.ucsd.edu, and use `javac` and `java` to compline and run this file. 



If you secceed, you should see something like this:



![scp](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/Scp.png)



## Setting an SSH Key



Next we gonna use `ssh-keygen` to make a key pair, this can help us to avoid enter the password when we login.



First, log in to your remote station and use `mkdir` command to crete a folder in remote station:

`mkdir .ssh`

Now use `exit` to log out.



Second, on your local station, run:

`ssh-keygen`

It will create a key pair in your local station. When it ask you to enter the address to save the key, the easiest way is just press "enter" to use the default address. 

When it ask for passphrase, you can just press "enter" to jump it. The passphrase is a personal password to protect your private key.

After you succeed, you should see a .ssh folder in your work path, which contaions id_rsa and id_rsa.pub



Third, use scp to copy your public key to server. Run command below in your client (**be careful with the username**):

`scp /Users/yourLocalUserName/.ssh/id_rsa.pub YourServerUserName@ieng6.ucsd.edu:~/.ssh/authorized_keys`



After you succeed, you should see something like this:



![Setting an SSH Key](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/SSH_Key.png)



Now you can login to the server without enter the password anymore.



## Optimizing Remote Running



Now, try to use ssh, in your **local station** to run some commands in **remote station**:

`ssh YourUserName@ieng6.ucsd.edu "ls"`



And you can run multiple commands in one line, like this:

`ssh YourUserName@ieng6.ucsd.edu "cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI"`



After you succeed, you should see something like this:



![more commands](https://ruili4ucsd.github.io/cse15l-lab-reports/lab01/Run_More_Commands.png)


