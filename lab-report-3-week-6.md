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
    * If the `config` file doesn't exist, you must first create it. From within the `.ssh` directory, type `touch config` to create the `config` file.

    **insert screenshot here**

* Then type `vim config` to edit the config file from the command line. Type `i` to enter Insert mode, so you can edit the contents of the file. This is what the screen should look like:

    **insert screenshot here**

* Paste the following in the file, replacing the `zzz` with your username:
```
Host ieng6
HostName ieng6.ucsd.edu
User cs15lsp22zzz
```

* When done editing, press the `ESC` key to return to Normal mode. To save, type `:w`, and to exit, type `:q` (you can type `:wq` to save and exit at the same time). 
* `ieng6` will now be your nickname for logging into the ieng6.ucsd.edu remote server.

* You should be able to log into the remote server with just `ssh ieng6`, instead of `ssh cs15lsp22zzz@ieng6.ucsd.edu`:

**insert screenshot here**

* Here is an example of copying a file from your local computer to the home directory of a remote server, using the newly streamlined nickname:

**insert screenshot here**


### 2. Setting up Github Access from a Remote Server (ieng6)<a name="part2"></a>



### 3. Copying Entire Directories with `scp -r`<a name="part3"></a>