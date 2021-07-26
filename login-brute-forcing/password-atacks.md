# Password Attacks

HTTP has two authentication mechanisms:
- `Basic HTTP AUTH` used to authicate the user to the HTTP server
- `Prozy Server Authentication` used to authenticate the user to an intermediate proxy server

### Basic HTTP Auth

This uses a  `user ID` and `password` for authentication.
1. Client send request _without authentication_ information
2. Server response contains `WWW-authenticate` header field. (The client will have to provide credentials here)
3. The client will use Base-64 to encode the identifier and password

### Types of Password Attack
- Dictionary Attacks
- Brute Force
- Traffic Injection
- Man in the Middle
- Key Logging
- Social Engineering


### Brute Force
A brute force attack doesn't depend on a wordlist. This is when we try every possible combination of the password.

For example, if we know a password is 3 characters long and only contains lower alphabet we would try:
- aaa
- aab
- aac
- ...
- zzz

Brute force attacks aren't the best type of attacks as if we only have lowercase letters, we can still have 26 options for each letter therefore we would have `26*n` options where n = the length of the  password. This would increase exponentially when uppercase letters, numbers, special characters etc. are added in as well.

#### Methods of Brute Force Atacks

| Attack  | Description  |
|---|---|
| Online Brute Force Attack  |  Attacking a live application over the network, like HTTP, HTTPs, SSH, FTP, and others |
| Offline Brute Force Attack  | Also known as Offline Password Cracking, where you attempt to crack a hash of an encrypted password.  |
| Reverse Brute Force Attack  | Also known as username brute-forcing, where you try a single common password with a list of usernames on a certain service.  |
| Hybrid Brute Force Attack  | Attacking a user by creating a customized password wordlist, built using known intelligence about the user or the service.  |

### Dictionary Attack
This is when we try to guess the passwords with the help of pre-made lists. The list would be a list of known, common passwords, which we would use to try and guess real password with.

One great place to get usernames / passwords would be [seclists](https://github.com/danielmiessler/SecLists "Seclists")
