# Chapter 2, Section 7: Getting Help

As always, the internet can provide a great source of information regarding different commands or commands not covered by this book. In the exam environment however you will not have access to the internet so should look to use the man pages or the documentation included in /usr/share/doc.

The man command (manual) can prove to be very useful in the exam environment if you forget a command. For example, the following command will display the man page entry for vi:

```
 [root@uk doc]# man vi
```

Within the man entry, you can use the arrow keys to navigate, along with the spacebar and page up or page down buttons. Also note that you can search for patterns just like in other editors such as less or more with a /pattern expression. You can also give man a keyword to search for or use the apropos command:

```
 [root@uk doc]# man -k vi
 [root@uk doc]# apropos vi
```

Once we find the command we are after, we can look at the man page specific to that command or use the specific help option of that command. Don't forget to run the mandb command to update the manual database before performing a search as the database may need to be updated.

The operating system also provide the whatis command for checking what commands do or to understand the file type of a specific file. For example:

```
[root@uk doc]# whatis usermod
usermod (8)          - modify a user account
```

Finally, the info command is available for browsing documentation distributed as part of the GNU Project. For example:

```
[root@uk doc]# whatis usermod
usermod (8)          - modify a user account
```

Will give you information about the passwd command for changing user passwords.
