# Question

```
Now our client wants to know if it is posible to fund out the version of hte running services. Submit the version of the service our client was talking about as the answer

Command:
First nmap it to find the right port (50000) with the database stuff which we want to access:
nmap -sV -sV 10.129.2.47

Then try make an NC connection to it:
sudo nc -nv 10.129.2.47 50000 -p 53

--> connection refused it is alreadu in use

Find out what is currently connected to it:
lsof -i :53 | grep 53

Result:
COMMAND   PID            USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd-r 646 systemd-resolve   17u  IPv4  10626      0t0  UDP 127.0.0.53:domain
systemd-r 646 systemd-resolve   18u  IPv4  10627      0t0  TCP 127.0.0.53:domain (LISTEN

Try these (googled this part):
sudo systemctl disable systemd-resolved.service
sudo systemctl stop systemd-resolved
nano /etc/NetworkManager/NetworkManager.conf
--> in here add in this line in the [main] section:
rm /etc/resolv.conf
sudo service networking restart

Make connection again to get the flag:
sudo nc -nv 10.129.2.47 50000 -p 53

Result:
Connection to 10.129.2.47 50000 port [tcp/*] succeeded!
220 HTB{kjnsdf2n982n1827eh76238s98di1w6}

Result:


Answer/Flag:

HTB{kjnsdf2n982n1827eh76238s98di1w6}

```
