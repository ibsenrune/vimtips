# VIM tips & tricks

## Moving around

### Going back and forth

If we consider a word to be any sequence of letters, numbers and the underscore character, we may 
navigate between words using these commands:

|Command|Effect|
|-------|------|
|`e`    | Go to the end of the word |
|`b`    | Go to the beginning of the word | 

This is not ideal when working with code, where we often want to skip special characters and not only words as defined above.
If we define WORDS to be sequences of characters delimieted by whitespace, we can use the following commands 
to move between these:

|Command|Effect|
|-------|------|
|`E`    | Go to the end of the WORD|
|`B`    | Go to the beginning of the WORD|

|Command|Effect|
|-------|------|
|`^`    | Go to the first non-whitespace character of the line |
|`$`    | Go to the last character of the line |
|`A`    | Go to the last character of the line and enter INSERT mode |

### Editing

#### Deleting text

|Command|Effect|
|-------|------|
|`dd`   | Delete current line|
|`dt.`  | Delete from current position until (not including) next `.` (on current line only)|
|`df.`  | Delete from current position until (and including) next `.` (on current line only)|

#### Copying and pasting

|Command|Effect|
|-------|------|
|`yt.`| Yank (copy) from current position until but not including next `.`|
|`yf.`| Yank (copy) from current position until and including next `.`|

## Visual Block Mode

Visual block mode allows you to edit a consecutive set of lines in one go. You enter Visual Block Mode, select a number of consecutive lines, perform the desired operation and then, when you hit `ESC`, the operation is performed on all the selected lines.

You enter Visual Block Mode by pressing `C-q`. Once in Visual Block Mode, you may select the lines to affect using the usual `h`, `j`, `k`, and `l` keys. Next, press `I` to place the cursor before the first selection and change to insert mode. You are now ready to insert something at the front of each line. Alternatively, press `A` to move the curser to the end of the line and change to insert mode, getting ready to append something to each line. Type whatever you want to insert. When you hit `ESC`, your changes will be performed on each selected line.

#### An aside: Visual Block Mode on Windows
On linux, you enter Visual Block Mode by pressing `C-v`. However, this key combination is used for pasting text on Windows, so VIM offers an alternative, `C-q`.

There is another caveat, though: `C-q` has a special meaning in some terminals, so if you run VIM in a terminal, the terminal may catch the `C-q` key combination. Thus, to be able to enter Visual Block Mode on Windows while running VIM in a terminal, you will have to unset this behaviour of your terminal. If you are running bash, you may do this by putting

```
stty start undef
```

in your `.bashrc` file.

## Tags

To create a `tags` file run 

```
ctags -R .
```

on the command line at the top of your project. Now, when using Vim, you may use `C-]` to go to the definition of a symbol.

# Diffing with VIM

To diff two files using VIM, start VIM with the `-d` option:

```
vim -d file1 file2
```

