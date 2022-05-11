# Permissions Cheat Sheet

## Permissions Structure

**There are three types of permissions in files and folders in Unix**

    1. Read    (r)
    2. Write   (w)
    3. Execute (x)
    
**And, there is a classification of users referred to as UGO**

    1. User    (U)
    2. Group   (G)
    3. Others  (O)
    
**When you run `$ ls -l` your output will look something like this...**

<img align="center" img width="718" alt="Screen Shot 2022-05-11 at 11 51 33 am" src="https://user-images.githubusercontent.com/72744507/167752785-f9ced595-4981-41fd-9068-81c208a0f319.png">

**The three sets of `rwx` coincide with the below table**

|| Read (R)      | Write (W)     | Execute (X)  |
|:------------:| :------------:| :------------:| :-----------:|
|Owner|       R       |       W       |       X      |
|Group|       R       |       W       |       X      |
|Others|       R       |       W       |       X      |

`rwxrwxrwx` means that user, group and others can read, write and execute

`rwxr-xr-x` means that the user can read, write and execute. The group and others can only read and execute

`rwx------` means that only the user can read, write and execute

`------` means that nobody can read, write or execute

## Changing File Permissions

**Each of the letters (rwx) coincide with a number, as per the below table**


|| Read (R)      | Write (W)     | Execute (X)  |
|:------------:| :------------:| :------------:| :-----------:|
|Owner|       4       |       2       |       1      |
|Group|       4       |       2       |       1      |
|Others|       4       |       2       |       1      |



**By running chmod using the above numbers, we can specify the permissions for each classification**

```shell
$ chmod [options] <permissions> <path>
```

`$ chmod 777 /Users/Admin/Desktop/date.txt` would give all classifications (UGO) access to read, write and execute

`$ chmod 755 /Users/Admin/Desktop/date.txt` would give the user access to read, write and execute, and the group and others access to only read and execute

## chmod Options


| Option     | Outcome     |
|------------|-------------| 
|-c| 	Like -v, but gives verbose output only when a change is actually made.|
|-f| 	Quiet mode; suppress most error messages.|
|-v| 	Verbose mode; output a diagnostic message for every file processed.|
|-R| 	Change files and directories recursively.|
|--help|	Display a help message and exit.|
|--version|	Output version information and exit.|

## Changing File Owners & Groups

Using the chown command, we can change the owner or group of a file.

```shell
$ chown [options] <user>:<group> <path>
```
`$ chown max.levey:admin /Users/Admin/Desktop/date.txt` would change the user to `max.levey` and the group to `admin` 

`$ chown max.levey /Users/Admin/Desktop/date.txt` would change the user to `max.levey` without effecting the group

`$ chown :admin /Users/Admin/Desktop/date.txt` would change the group to `admin` without effecting the user

**We can also change owners on files specifically owned by another user with `--from`**

```shell
$ chown --from=<existing_user> <user> <path>
```
`$ chown --from=max.levey root /Users/Admin/Desktop/date.txt` would change the user to `root` **if** the file user is `max.levey`

**The same can be done for groups**

```shell
$ chown --from=:<existing_group> :<group> <path>
```
`$ chown --from=:admin :wheel /Users/Admin/Desktop/date.txt` would change the group to `wheel` **if** the file group is `admin`

## chown Options


| Option     | Outcome     |
|------------|-------------| 
|-c| 	Like -v, but gives verbose output only when a change is actually made.|
--from| Change the owner or group of each file only if its current owner or group match those specified.
|-f| 	Quiet mode; suppress most error messages.|
|-v| 	Verbose mode; output a diagnostic message for every file processed.|
|-R| 	Change files and directories recursively.|
|--help|	Display a help message and exit.|
|--version|	Output version information and exit.|

