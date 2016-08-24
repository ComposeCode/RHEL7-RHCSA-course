# Chapter 2, Section 6: Working and Editing Text

The vi (vim) editor is an interactive visual text editor which comes with most unix systems. It can be used as a fully fledged editor in a terminal for editing config files, code or other files.

To start vi, run the command vi in a terminal, the editor will open. If you want to open an existing file in the editor, use the command like this:

```
[root@uk ~]# vi /etc/hosts
```

You can do this with files which don't exist as well and a new file will be automatically created when it is saved. There are several modes of operation in vi: Command mode, edit mode and the last line mode.

To enter text mode issue one of the commands by pressing the relevant key: i (insert text before current cursor position), I (insert text at the beginning of the current line), a (appends text after the current cursor position), A (appends text at the end of the current line), o (opens up a new line below the current line), O (opens up a new line above the current line).

To exit text mode, hit the escape key and you will return command mode.

-- need: navigation vi, deleting text, undo/repeat, c+p, search and replace, undo, saving, changing text, quitting. 

wc
grep
awk
vi
