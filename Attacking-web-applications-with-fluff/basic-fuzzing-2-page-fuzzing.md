# Page Fuzzing
This is what we do in order to locate pages.

## Extension Fuzzing
This is when we try to fuzz in order to find out extensions are used by the directories e.g. `.html`, `.aspx`, `.php`

You are sometimes able to guess what these extensions are, for example, `apache` is likely to be `.php`, `IIS` is often `.asp` or `.aspx` etc. However, this can take a long time. We can use `ffuf` to do this instead.

e.g.
```
ffuf -w /opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt:FUZZ <SNIP>

ffuf -w /opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt:FUZZ -u http://SERVER_IP:PORT/blog/indexFUZZ
```
# Question
Try to use what you learned in this section to fuzz the '/blog' directory and find all pages. One of them should contain a flag. What is the flag?
```


Answer:


```

ffuf -w /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/blog/FUZZ.php
