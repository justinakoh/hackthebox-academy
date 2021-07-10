# NMAP
Nmap is used for enumeration. It can tell you lots of invalueable information about the target such as any known vulnerabilities it might have, what systems it's running etc.
In order to use nmap, the basic structure for NMAP is:

```
nmap <scan types> <options> <target>
```
There are many settings that you can use.
- `-sS (TCP-SYN scan)` is a default setting. This allows you to scan thousands of ports per second. It sends one packet with the SYN flag so that a connection isn't made with the port

## Host Discovery
If you need to discover an entire network, you need to get an overview of the systems that you want to work with. When you're doing these scans it is recommended that you save the results.

### Scanning a Network Range:

This is an example of a scan that you could do:
```
$ sudo nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5
```
- `-sn` disables port scan
- `-oA`
- `tnet`

Alternatively, if you have a list of IP addresses that you want to scan, you can also create a list and scan them that way:

```
$ sudo nmap -sn -oA tnet -iL hosts.lst | grep for | cut -d" " -f5
```
Given that your list is called `hosts.lst` and that `-iL` means that you're going to give it a list of addresses to scan.

Another way is to list out the IP addresses instead of passing a list in. In that case you would have the same command as above, but instead, you would have the IP addresses listed out like so:
```
$ sudo nmap -sn -oA tnet 10.129.2.18 10.129.2.19 10.129.2.20| grep for | cut -d" " -f5
```
OR
```
$ sudo nmap -sn -oA tnet 10.129.2.18-20| grep for | cut -d" " -f5

10.129.2.18
10.129.2.19
10.129.2.20
```

### Scanning Single IP Addresses:
If you want to check whether a single host is alive or not (so that we can proceed to check its ports etc.) you can use the following:
```
$ sudo nmap 10.129.2.18 -sn -oA host

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-14 23:59 CEST
Nmap scan report for 10.129.2.18
Host is up (0.087s latency).
MAC Address: DE:AD:00:00:BE:EF
Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
```
When you disable port scan `-sn` it pings with `ICMP Echo Requests`. If the host is alive, it will reply with a` ICMP reply`.

Another way to check if it is alive is `--reason`
```
$ sudo nmap 10.129.2.18 -sn -oA host -PE --reason

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-15 00:10 CEST
SENT (0.0074s) ARP who-has 10.129.2.18 tell 10.10.14.2
RCVD (0.0309s) ARP reply 10.129.2.18 is-at DE:AD:00:00:BE:EF
Nmap scan report for 10.129.2.18
Host is up, received arp-response (0.028s latency).
MAC Address: DE:AD:00:00:BE:EF
Nmap done: 1 IP address (1 host up) scanned in 0.03 seconds
```

In order to check the type of reply that you have + what you sent you can use `--packet-trace`. To check whether `ICMP echo` requests are also made you can use `-PE`

```
$ sudo nmap 10.129.2.18 -sn -oA host -PE --packet-trace

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-15 00:08 CEST
SENT (0.0074s) ARP who-has 10.129.2.18 tell 10.10.14.2
RCVD (0.0309s) ARP reply 10.129.2.18 is-at DE:AD:00:00:BE:EF
Nmap scan report for 10.129.2.18
Host is up (0.023s latency).
MAC Address: DE:AD:00:00:BE:EF
Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds
```


### Used Scanning Techniques
We can disable the ARP pings by setting the `--disable-arp-ping` option.
```
$ sudo nmap 10.129.2.18 -sn -oA host -PE --packet-trace --disable-arp-ping

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-15 00:12 CEST
SENT (0.0107s) ICMP [10.10.14.2 > 10.129.2.18 Echo request (type=8/code=0) id=13607 seq=0] IP [ttl=255 id=23541 iplen=28 ]
RCVD (0.0152s) ICMP [10.129.2.18 > 10.10.14.2 Echo reply (type=0/code=0) id=13607 seq=0] IP [ttl=128 id=40622 iplen=28 ]
Nmap scan report for 10.129.2.18
Host is up (0.086s latency).
MAC Address: DE:AD:00:00:BE:EF
Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
```

## Question:

 Based on the last result, find out which operating system it belongs to. Submit the name of the operating system as result.

 `Windows`

 We know this because the reply is `ICMP`, and it took 128 seconds
