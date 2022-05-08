# Lab Report 3
## Streamlining `ssh`, Remote Github Access, Copying Entire Directories
--- 
In this lab report, we will go over the following topics:
1. [Streamlining `ssh` Configuration](#part1)
2. [Setting up Github Access from a Remote Server (ieng6)](#part2)
3. [Copying Entire Directories with `scp -r`](#part3)

---
### 1. Streamlining `ssh` Configuration<a name="part1"></a>
* Navigate to ~/.ssh/config from your terminal using `cd ~/.ssh/config`.
    * If the `config` file doesn't exist, you must first create it. From within the `.ssh` directory, type `touch config` to create the `config` file:

    ![creating config file](https://user-images.githubusercontent.com/103291789/167241506-03ddbc02-8b8b-45c3-8c0c-dbfc24edba85.jpeg)

* Then type `vim config` to edit the config file from the command line. Type `i` to enter Insert mode, so you can edit the contents of the file. This is what the screen should look like:

![vim insert mode](https://user-images.githubusercontent.com/103291789/167241551-dd932f35-c9fd-4ce4-8e89-a414e958a181.jpeg)

* Paste the following in the file, replacing the `zzz` with your username:
```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22zzz
```

* When done editing, press the `ESC` key to return to Normal mode. To save, type `:w`, and to exit, type `:q` (you can type `:wq` to save and exit at the same time). 
* `ieng6` will now be your nickname for logging into the ieng6.ucsd.edu remote server.
* You should be able to log into the remote server with just `ssh ieng6`, instead of `ssh cs15lsp22zzz@ieng6.ucsd.edu`:

![streamlined log in](https://user-images.githubusercontent.com/103291789/167241587-19c819be-b8ac-4052-9ce4-6b46cca957b7.jpeg)

* Here is an example of copying a file (FileToCopy.java) from your local computer to the home directory of a remote server, using the newly streamlined nickname:

![scp with nickname](https://user-images.githubusercontent.com/103291789/167241598-67e3b831-57d0-4344-b0e1-c59949ee1b02.jpeg)

### 2. Setting up Github Access from a Remote Server (ieng6)<a name="part2"></a>
* From your ieng6 account, run `ssh keygen` to generate a new pair of public and private keys. Follow [this tutorial](https://isabelwang30.github.io/cse15l-lab-reports/lab-report-1-week-2.html#part5) from Lab Report 1 if needed.
* Then use the command `pbcopy < ~/.ssh/id_rsa.pub` (replacing the `id_rsa.pub` with the name of your public key if applicable) to copy the contents of the public key to your clipboard.
    * If the `pbcopy` command doesn't work, navigate to the `.ssh` directory, and use `cat id_rsa.pub` to get the contents of the public key.
* Go to Github and go to your accound settings. Under the Access section, click **SSH and GPG keys**. Click **New SSH key**, and then give the key a title, such as `ieng6`. Then paste the contents of the public key into the **Key** section, and click **Add SSH key**. 
* This is where the public key is stored in Github:

![SSH key in Github](https://user-images.githubusercontent.com/103291789/167282139-c4177299-3811-4504-b4d0-8eb48c40be4c.jpeg)

* The public and private keys are stored in the hidden `.ssh` folder in your ieng6 account:

![.ssh in ieng6](https://user-images.githubusercontent.com/103291789/167282151-5dbb4ba0-e37c-43d5-89a3-beb2e66dc9d1.jpeg)

* Now you should be able to commit and push changes to Github from the ieng6 remote server. Here is an example of what that looks like:

![change to SSH url](https://user-images.githubusercontent.com/103291789/167282164-7761e01f-c89d-4839-b2bc-8436a4d54676.jpeg)
![commit and push from ieng6](https://user-images.githubusercontent.com/103291789/167282175-3b3fbf8d-7786-44d0-8f00-80319ed8e7d2.jpeg)

* First make sure the remote URL is the SSH one, not the HTTPS one.
* The edit I made to MarkdownParseTest.java was appending "test" to the file.
* Here is a [link](https://github.com/isabelwang30/markdown-parser/commit/512164731c6fe532a85d3e1a9908852129daddeb) to the resulting commit.

### 3. Copying Entire Directories with `scp -r`<a name="part3"></a>
* To recursively copy an entire directory – which includes all the files and directories within it, as well as all the files and directories within those, etc – use the a command such as `scp -r . ieng6:~/markdown-parse`.
    * The `-r` tells the `scp` to work recursively, the `.` is the current working directory (the directory to be copied), the `ieng6` is the nickname for the remote server to be copied to, and the `~/markdown-parse` is the path where the directory will be copied to on ieng6.
* Here is an example of copying an entire directory to a new directory called `markdown-parser` in my ieng6 account:

![scp -r (entire directory)](https://user-images.githubusercontent.com/103291789/167284737-577ea5a6-b7ea-4e47-b37f-78f5ec10be86.jpeg)
(there were many other files copied over that aren't included in the screenshot)

* Here is what it looks like to then log into the remote server and compile and run the Test file in the directory:

![running copied tests from ieng6](https://user-images.githubusercontent.com/103291789/167284767-1fc0bd4f-7ecb-4ad9-afe4-77acabc7be09.jpeg)

* All the commands can also be combined into one line, but in order to run the Test file successfully, a couple changes need to be made.
    1. Instead of copying the entire directory, only copy files ending with `.java` or `.md`, and everythig in the `lib` directory (JUnit files).
    2. Because you are no longer copying the entire directory, the destination directory in the remote server needs to exist prior to using `scp -r`; a new directory won't be automatically created with this `scp -r` command.
    3. Then, to compile and run the Test file, replace the `javac` with `/software/CSE/oracle-java-17/jdk-17.0.1/bin/javac`, and replace the `java` with `/software/CSE/oracle-java-17/jdk-17.0.1/bin/java`.
* Here is what combining all the commands looked like for me (after deleting the `markdown-parse` directory created with the previous `scp -r` command:

![C7987EEB-B2E6-4F2D-8BCA-CD759AD14756](https://user-images.githubusercontent.com/103291789/167284782-810c8841-a466-440a-9190-84b4846593f0.jpeg)
