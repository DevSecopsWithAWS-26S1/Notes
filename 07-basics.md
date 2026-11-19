## CRUD operations

CRUD means Create, Read, Update, and Delete.

| Operation | Command |
|---|---|
| Create a file | `touch <filename>` |
| Create a directory | `mkdir <directory>` |
| Read a file | `cat <filename>` |
| Delete a file | `rm <filename>` |
| Force-delete a file | `rm -f <filename>` |
| Delete a directory recursively | `rm -rf <directory>` |

## Copy and move files

The general pattern is: copy or move the source to the destination.

```sh
cp training.txt ./folder1/  # Copy
mv training.txt ./folder1/  # Move
```


### Edit a file

Use `vi` or `vim` to update file content.

* `Shift+G` - Go to the end of the file
* `gg` - Go to the beginning of the file


#### Command mode

* `:/<pattern>` - Search forward
* `:?<pattern>` - Search backward
* `n` - Next match
* `N` - Previous match

* :set nu - Show line numbers in the file   
* :set nonu - Hide line numbers in the file
* :q - Quit the editor without saving the changes
* :wq - Save the changes and quit the editor

* :q! - Quit the editor without saving the changes (force quit)
* wq! - Save the changes and quit the editor (force save and quit)

* :s/<Search>/<Replace>/g - Search and replace a specific word in the file
* :s/<Search>/<Replace>/gc - Search and replace a specific word in the file with confirmation for each replacement


#### Normal mode
* Esc + i - Insert mode (to insert text)
* Esc + u - Undo the last change
* yy - Copy the current line
* dd - Delete the current line
* p - Paste the copied line below the current line
* 2p - Paste the copied line 2 times below the current line
* `Esc + 1,$d` - Delete all lines

