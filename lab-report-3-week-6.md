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


* Here is an example of copying a file from your local computer to the home directory of a remote server, using the newly streamlined nickname:

![scp with nickname](https://user-images.githubusercontent.com/103291789/167241598-67e3b831-57d0-4344-b0e1-c59949ee1b02.jpeg)

### 2. Setting up Github Access from a Remote Server (ieng6)<a name="part2"></a>



### 3. Copying Entire Directories with `scp -r`<a name="part3"></a>
