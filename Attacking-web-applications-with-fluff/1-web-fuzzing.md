# Web Fuzzing

## Fuzzing

Fuzzing is testing technique which sends out various types of user input to a certain interface to see how it would react.

e.g. SQL injection fuzzing would mean that you send a bunch of random special characterrs to a server to see it how it reccts.

For webservers, when you are trying to fuzz directories (figure out what directories it has) it has you would append a bunch of stuff to the main URL and see if you get a `200 found`. If it doesn't exist, then you would get a `404 Page Not Found`.


## Wordlists

These are used to help speed up the process of finding directories. They might not return back _all_ the directoires that exist, as technicalyl the creators of the website could name their directories whatever they like e.g. _google.com/unicorns-in-thailand_, however, wordlists usually contain the most common directories and can get up to 90% success rate.

We have a wordlist that we will be using for this module:
- `directory-list-2.3-small.txt`

## Removing Comments
```
sudo sed -i 's/^\#.*$//g' /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt && sudo sed -i '/^$/d' /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt
Table of Contents
Introduction
Basic Fuzzing
Domain Fuzzing
Parameter Fuzzing
Skills Assessment
My Workstation
OFFLINE

 / 1 spawns left
```
