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

```shell
$ls -l /Users/Admin/Desktop/date.txt

rwxrwxrwx user group date.txt
```

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

`$ chmod [options] <permissions> <file>`

`
$ chmod 777 /Users/Admin/Desktop/date.txt` would give all classifications (UGO) access to read, write and execute

```shell
$ls -l /Users/Admin/Desktop/date.txt

rwxrwxrwx user group date.txt
```


`
$ chmod 755 /Users/Admin/Desktop/date.txt` would give the user access to read, write and execute, and the group and others access to only read and execute

```shell
$ls -l /Users/Admin/Desktop/date.txt

rwxr-xr-x user group date.txt
```

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

