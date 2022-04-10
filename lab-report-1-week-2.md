# Lab Report 1
## VSCode, Basic UNIX Commands, and Remote Access on MacOS
---

### 1. Installing VSCode
* Go to the [VSCode website](https://code.visualstudio.com/) and download the version corresponding to your computer's operating system. 
* After downloading, the home screen should look similar to this:
![VSCode home screen](https://user-images.githubusercontent.com/103291789/162599617-b0eced60-730e-4f88-b6df-977943fff0ed.jpeg)


### 2. Remotely Connecting
* Go to [this website](https://sdacs.ucsd.edu/~icc/index.php) to look up your CSE 15L username.
* Then, in VSCode, open a terminal and use the command `ssh cs15lsp22xxx@ieng6.ucsd.edu`, with the `xxx` replaced with the letters in your own username.
* Respond `yes` to the prompt asking if you want to continue connecting, and then enter your password.
* Once you are connected, you should see something like this in your terminal: ![Successful Remote Connection](https://user-images.githubusercontent.com/103291789/162599627-65a638c8-611b-4673-b4b8-4b45c08877ac.jpeg) 


### 3. Trying Some Commands
* Next, you can try running some basic UNIX commands from your VSCode terminal. For example:
    * `cd ~` will change the directory back to your home directory
    * `ls` will list the files in your current directory
    * `ls -a` will list all files, including hidden ones, in your current directory
 * This is what I get when I run `ls` and `ls -a`:
![`ls` and `ls -a` commands](https://user-images.githubusercontent.com/103291789/162599771-a2fdc392-2744-48cf-a8c1-eab57c3056fb.jpeg)

* Some other commands to try include:
    *  `ls -l`
    *  `ls -t`
    *  `ls -lat`
    *  `ls -l`
    *  `ls -l`
* To log out of the remote server, use Ctrl + D or use the `exit` command


### 4. Moving Files with `scp`
* 


### 5. Setting an SSH Key
* 


### 6. Optimizing Remote Running
* 



