# Personalised Wordlists

You can create personalised wordlists. To do this you need to get information about them. We can use `CUPP` to do this


### CUPP
This is particularly handy when you are trying to attack a specific person that you know information about. To do this, you just run `cupp -i` to run it in interactive mode, then you can just follow and enter information as the prompts appear. This will then generate a password list customised to the person you just entered all the details about.


As the password list generated is about 43 000 lines long, there will be lots of stuff that might not be relevant i.e. if the password isn't long enough, or it doesn't have the correct characters etc. in it. To remove this, we can write the following lines of code in a bash file, then run it.

```
sed -ri '/^.{,7}$/d' william.txt            # remove shorter than 8
sed -ri '/[!-/:-@\[-`\{-~]+/!d' william.txt # remove no special chars
sed -ri '/[0-9]+/!d' william.txt            # remove no numbers
```


### Mangling
This is when you try as many variations of the wordlist that you have as possible. It will chop things up, mangle them up, swap it up etc. so that the wordlist is as varied as possible.


### Usernames
You can also create custom wordlists for usernames as well. You can use `https://github.com/21y4d/usernameGenerator.git` to create these.

To use username generator you would use it like this:
```
bash usernameGenerator/usernameGenerator.sh firstname lastname

e.g.
bash usernameGenerator/usernameGenerator.sh Bill Gates
```
