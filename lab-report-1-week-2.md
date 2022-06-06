[< Home](https://isabelwang30.github.io/cse15l-lab-reports/)
# Lab Report 1
## VSCode, Basic UNIX Commands, and Remote Access on MacOS
---
In this lab report, we will go over the following topics:
1. [Installing VSCode](#part1)
2. [Remotely Connecting](#part2)
3. [Trying Some Commands](#part3)
4. [Moving Files with `scp`](#part4)
5. [Setting an SSH Key](#part5)
6. [Optimizing Remote Running](#part6)

---
### 1. Installing VSCode<a name="part1"></a>
* Go to the [VSCode website](https://code.visualstudio.com/) and download the version corresponding to your computer's operating system. 
* After downloading, the home screen should look similar to this:

![VSCode home screen](https://user-images.githubusercontent.com/103291789/162599617-b0eced60-730e-4f88-b6df-977943fff0ed.jpeg)


### 2. Remotely Connecting<a name="part2"></a>
* Go to [this website](https://sdacs.ucsd.edu/~icc/index.php) to look up your CSE 15L username.
* Then, in VSCode, open a terminal and use the command `ssh cs15lsp22xxx@ieng6.ucsd.edu`, with the `xxx` replaced with the letters in your own username, to connect to the `ieng6` server.
* Respond `yes` to the prompt asking if you want to continue connecting, and then enter your password.
* Once you are connected, you should see something like this in your terminal: 

![Successful Remote Connection](https://user-images.githubusercontent.com/103291789/162599627-65a638c8-611b-4673-b4b8-4b45c08877ac.jpeg) 


### 3. Trying Some Commands<a name="part3"></a>
* Next, you can try running some basic UNIX commands from your VSCode terminal. For example:
    * `cd ~` will change the directory back to your home directory.
    * `ls` will list the files in your current directory.
    * `ls -a` will list all files, including hidden ones, in your current directory.
 * This is what I get when I run `ls` and `ls -a`:

![`ls` and `ls -a` commands](https://user-images.githubusercontent.com/103291789/162599771-a2fdc392-2744-48cf-a8c1-eab57c3056fb.jpeg)

* Some other commands to try include:
    *  `ls -l`
    *  `ls -t`
    *  `ls -lat`
    *  `ls -l`
    *  `ls -l`
* To log out of the remote server, use Ctrl + D or use the `exit` command.


### 4. Moving Files with `scp`<a name="part4"></a>
* Create a file on your computer called `WhereAmI.java` and paste the following code into it:
```
class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
    }
}
```
* Assuming you have Java installed, run this file on your computer (the client), using `javac` and `java` commands. You should get something like this: 

![WhereAmI.java on client](https://user-images.githubusercontent.com/103291789/162601320-41baa400-7344-417d-8acb-bb61f4e30b67.jpeg)

* From the directory where you made the `WhereAmI.java` file, run this command with your username: `scp WhereAmI.java cs15lsp22xxx@ieng6.ucsd.edu:~/`. Enter your password when prompted. This copies the file to the server!
* Using `ssh`, log into `ieng6` again, and run the file from there using `javac` and `java`. Now, you should get something like this: 

![WhereAmI.java on server](https://user-images.githubusercontent.com/103291789/162601377-513e644e-48d5-44c3-b21a-b360c5c76129.jpeg)

* To copy multiple files at once, just list the file names separated by spaces after the `scp` command and before the destination.


### 5. Setting an SSH Key<a name="part5"></a>
* On your computer, run `ssh-keygen`. Copy and paste the file given in parentheses when prompted: 

![ssh keygen](https://user-images.githubusercontent.com/103291789/162601404-f684e534-16f9-468b-a197-8110625cebf1.jpeg)

* **Do NOT add a passphrase when prompted.** Just hit 'enter' both times.
    * You should get messages that indicate this process was successful, followed by a randomart image for the public key.
* To copy the public key to the `.ssh` directory of your account on the `ieng6` server, do the following:
    * Log into the server and enter `mkdir .ssh`. Then log out of the server.
    * On your computer, enter `scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22xxx@ieng6.ucsd.edu:~/.ssh/authorized_keys`. (The first part after the `scp` should be what you copied and pasted in step 1, with `.pub` added at the end).
* Now you can `ssh` and `scp` from your computer to the server without entering your password!


### 6. Optimizing Remote Running<a name="part6"></a>
* Use the up arrow on your keyboard to scroll through previous commands you've run.
* To run multiple commands in the same line, separate them with `;`.
    * For example: `javac WhereAmI.java; java WhereAmI` as seen in the above screenshot.
* You can log into a remote server, run a command (or commands) directly on that server, and then log out of the server all in one line:
    * After your `ssh` command, write the command(s) you want to run on the server in quotes.
    * For example:
    
    ![command in quotes](https://user-images.githubusercontent.com/103291789/162632312-8fccf9c7-0414-4766-bb25-3fc45eafffae.jpeg)
    
* Here are two examples of optimizing remote running:
   * The first command copies `WhereAmI.java` to the server. The second command securely logs into the server, compiles and runs the file, and logs out.
   * The third command combines the first two commands into one line, as explained above.

![optimizing remote running](https://user-images.githubusercontent.com/103291789/162632332-2f905c91-a831-48f4-a2e2-febd80283341.jpeg)
