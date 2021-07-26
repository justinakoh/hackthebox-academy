# Intro to Brute Forcing

A brute force attack is a method of attempting to guess passwords or keys by autmoated probing. E.g. Password cracking, credential guessing etc.

List of Files with hashed passwords:
```
Windows:

unattended.xml
sysprep.inf
SAM

Linux:

shadow
shadow.bak
password
```

You can't calculate something from a hash, therefore brute forcing hases will guess hash values belonging to randomly selected passwords until a hash matches one of the stored hash values. --> This is also known as `onlienn brute-forcing`

Tools for brute forcing:
- ncrack
- wfuzz
- medusa
- patator
- hydra
