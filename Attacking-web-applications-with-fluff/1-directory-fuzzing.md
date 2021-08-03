# Directory Fuzzing

Installing FFUF
```
sudo apt-get update
sudo apt-get upgrade
sudo apt install fuff -y
```


The most basic fuzzing command is:
```
ffuf -w <wordlist>:<keyword>

e.g.
ffuf -w /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ
```
- `-w` lets us pick the wordlist we want to use to fuzz with

If you want to fuzz a web directory you can do:

```
ffuf -w <SNIP> -u http://SERVER_IP:PORT/FUZZ
```

# Question

In addition to the direcory we found above, there is another diretory that can be found. What is it?

```
Command:
ffuf -w /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://46.101.23.188:31862/FUZZ


Result:
/'___\  /'___\           /'___\       
/\ \__/ /\ \__/  __  __  /\ \__/       
\ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
\ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
 \ \_\   \ \_\  \ \____/  \ \_\       
  \/_/    \/_/   \/___/    \/_/       

v1.1.0-git
________________________________________________

:: Method           : GET
:: URL              : http://46.101.23.188:31862/FUZZ
:: Wordlist         : FUZZ: /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
:: Follow redirects : false
:: Calibration      : false
:: Timeout          : 10
:: Threads          : 40
:: Matcher          : Response status: 200,204,301,302,307,401,403
________________________________________________

# Copyright 2007 James Fisher [Status: 200, Size: 986, Words: 423, Lines: 56]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56]
# directory-list-2.3-small.txt [Status: 200, Size: 986, Words: 423, Lines: 56]
forum                   [Status: 301, Size: 323, Words: 20, Lines: 10]
# or send a letter to Creative Commons, 171 Second Street,  [Status: 200, Size: 986, Words: 423, Lines: 56]
# Priority ordered case sensative list, where entries were found  [Status: 200, Size: 986, Words: 423, Lines: 56]
blog                    [Status: 301, Size: 322, Words: 20, Lines: 10]
# on atleast 3 different hosts [Status: 200, Size: 986, Words: 423, Lines: 56]
# This work is licensed under the Creative Commons  [Status: 200, Size: 986, Words: 423, Lines: 56]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56]
# license, visit http://creativecommons.org/licenses/by-sa/3.0/  [Status: 200, Size: 986, Words: 423, Lines: 56]
# Suite 300, San Francisco, California, 94105, USA. [Status: 200, Size: 986, Words: 423, Lines: 56]
#                       [Status: 200, Size: 986, Words: 423, Lines: 56]
                [Status: 200, Size: 986, Words: 423, Lines: 56]
# Attribution-Share Alike 3.0 License. To view a copy of this  [Status: 200, Size: 986, Words: 423, Lines: 56]
                [Status: 200, Size: 986, Words: 423, Lines: 56]
:: Progress: [87664/87664] :: Job [1/1] :: 2138 req/sec :: Duration: [0:00:41] :: Errors: 0 ::


Answer:
forum

Alternate answer:
gobuster -u http://46.101.23.188:31862/ -w directory-list-2.3-small.txt -s 200

```
