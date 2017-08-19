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

