# Chapter 8 Section 1: Managing Users and groups

- Explain the passwd file (explain the format aswell)
- Explain the shadow file (explain the format aswell)
- Explain difference between the two
- Explain the group file (and format)
- Explain the gshadow file (and format)
- Example of pwck command + grpck command
- Example of using vipw and vigr instead of regular vi to prevent password corruption

# Creating/Removing/Chaning user accounts
- Useradd/mod/del/change/passwd examples for modifying users

- Useradd: -b (--base-dir, base dir for all home directories), -m (--create-home option),  groups etc

- the chage command (with examples):  -d --lastday, --expiredate --inactive
- chage -l chartwell option (display defaults)

- login.defs files + /etc/default/useradd
- changing defaults through useradd -D ...

# Usermod command
- explain usermod, add examples of using the command.

# Groupadd commands
- example of using groupadd/mod/del

# Switching users with su
- examples of su (touched on previously)
- examples of exiting sudoers file

# Shell defaults (bash rc)
- bashrc/profile etc
- examples of creating aliases
