# Linux File and Folder Permissions

Linux permissions control who can **read**, **write**, or **run/access** a file or folder.

## The 4-2-1 permission values

```text
r = read     4
w = write    2
x = execute  1
```

Add the values to combine permissions:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4     + 1 = 5
r-- = 4           = 4
```

## Who gets permissions?

```text
                 WHO
        ┌─────────┼─────────┐
      Owner      Group     Others
        │          │          │
       rwx        rwx        rwx
       421        421        421
```

A permission number has three digits: **owner**, **group**, and **others**.

For example, `754` means:

```text
Owner: 7 = rwx = read, write, execute
Group: 5 = r-x = read, execute
Others: 4 = r-- = read only
```

You can see permissions with:

```bash
ls -l
```

Example output:

```text
-rwxr-xr-- 1 alice developers 1200 Nov 26 09:00 script.sh
```

The first character indicates the type: `-` means a regular file, and `d` means a directory. The next nine characters show permissions for the owner, group, and others.

## File and folder permissions

| Permission | On a file | On a folder |
|---|---|---|
| `r` (read) | View the file contents | List names inside |
| `w` (write) | Change the file contents | Create, delete, or rename items inside |
| `x` (execute) | Run it as a program or script | Enter the folder and access items inside |

On a folder, `x` means permission to enter or search through it. It is generally needed to access items inside.

## Change permissions with `chmod`

Use `chmod` to change permissions:

```bash
chmod 754 myfile
```

This gives the owner `rwx`, the group `r-x`, and others `r--`.

To apply permissions to a folder and everything inside it:

```bash
chmod -R 755 myfolder
```

Use `-R` carefully: it applies the change recursively to all contents.

## Change owner and group with `chown`

Use `chown` to change who owns a file or folder:

```bash
sudo chown alice myfile
```

This changes the owner to `alice`.

To change both the owner and group:

```bash
sudo chown alice:developers myfile
```

To change ownership of a folder and everything inside it:

```bash
sudo chown -R alice:developers myfolder
```

Use `-R` carefully because it changes ownership recursively.

Check the current owner and group with:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 alice developers 1200 Nov 26 09:00 myfile
```

Here, `alice` is the owner and `developers` is the group.

## Quick reminder

```text
chmod = change permissions
chown = change owner and group
```
