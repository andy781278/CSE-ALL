Efficient text editor available via terminal to almost any OS.

Shortcuts:
##### Movement
k - up
j - down
h - left
l - right

0 - move to start of the line

##### Actions
x - delete
i - insert
r - replace
R - replace until escape
a - append
A - append at the end of line
e - go to end of this word
w - go to start of the next word
$ - go to end of line
u - undo action
U - undo everything on this line
ctrl r - redo
p - paste
o - make line under cursor, edit the line
O - make line above cursor, edit the line

`/phrase` - search the first instance of phrase after cursor
- n to go to the next one
- N to go to the previous one
- ? to search backwards, then n becomes go to the previous one, and N becomes go to the next one
- ctrl o - go back to where you came from
- ctrl i - go forward
- \c right after phrase to ignore case just for this search
- :set - sets some options for the search
	- :set ic - ignore cases
	- :set hls - highlights all found
	- :set is - includes partial words
	- :noic - cancels ic
	- :nohlsearch - cancels highlight

% - find the other matching bracket/parenthesis, any of these: ()[]{}

`d number motion`
d - delete operator and also cut operator
number - how many times to compute the motion
motion - what to delete
- dw - delete until the start of the next word
- de - delete until just after the end of this word
- d$ - delete everything after the cursor on that line
- dd - delete line

`c number motion` (delete + insert)
c - change operator
number - how many times to compute the motion
motion - what to change
- cw - delete until the start of the next word then inserts
- ce - delete until just after the end of this word then inserts
- c$ - delete everything after the cursor on that line then inserts
- cc - delete line then inserts

`y number motion`
y - copy operator
- yw - copy one word
- yy - copy whole line

v - visual selection / highlighter
- after highlighting, you can:
	- d to delete
	- :w filename to save this specific selection under filename
	- 

: - command
:w filename - saves this current doc under filename
:r filename - inserts the content of filename to cursor
:wq - save and quit
:q! - leave no save
:qa! - leave no save
:q - close window
:! command - executes command on regular terminal outside the vim
- ctrl d - lists possible commands based on what is written so far
- tab - autocompletes if possible

ctrl g - command
- G - go to start of the file
- gg - go to end of the file
- g n - go to line n

:help - opens the help manual