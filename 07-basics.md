## CRUD Operations
* Create , Read , Update , Delete 

* touch <filename> - Create a new file
* mkdir <directoryname> - Create a new directory
* cat <filename> - Read the contents of a file
* rm <filename> - Delete a file
* rm -f <filename> - Force delete a file
* rm -rf <directoryname> - Force delete a directory and its contents

* source & destination 
* where to which 
* cp training.txt ./folder1/  - Copy a file to a different directory
* mv training.txt ./folder1/  - Move a file to a different directory


### update a file
* vi editor is for updating the file content

* shift + G  - Go to the end of the file
* gg - Go to the beginning of the fil


#### : mode 
* :/ - search from top of the file 
* if there are multiple matches , use ```n``` to go to next match and N to go to previous match

* :? - search from bottom of the file 
* if there are multiple matches , use ```n``` to go to next match and N to go to previous match

* :set nu - Show line numbers in the file   
* :set nonu - Hide line numbers in the file
* :q - Quit the editor without saving the changes
* :wq - Save the changes and quit the editor

* :q! - Quit the editor without saving the changes (force quit)
* wq! - Save the changes and quit the editor (force save and quit)

* :s/<Search>/<Replace>/g - Search and replace a specific word in the file
* :s/<Search>/<Replace>/gc - Search and replace a specific word in the file with confirmation for each replacement


#### ESC MODE :
* Esc + i - Insert mode (to insert text)
* Esc + u - Undo the last change
* yy - Copy the current line
* dd - Delete the current line
* p - Paste the copied line below the current line
* 2p - Paste the copied line 2 times below the current line
* Esc + 1,$d - remove all lines 


## Tommorow we will practice the following commands :

* head <filename> - Display the first 10 lines of a file
* head -n 5 <filename> - Display the first 5 lines of a file


* tail <filename> - Display the last 10 lines of a file
* tail -n 5 <filename> - Display the last 5 lines of a file

* grep <pattern> <filename> - Search for a specific pattern in a file
* grep -i <pattern> <filename> - Search for a specific pattern in a file (case-insensitive)
* grep -r <pattern> <directory> - Search for a specific pattern in all files    


* wget <url> - Download a file from the internet


* cut & awk  - these are used to extract specific columns or fields from a file or output.

