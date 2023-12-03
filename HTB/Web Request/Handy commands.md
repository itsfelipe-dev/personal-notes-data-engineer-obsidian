Another handy method for scanning ports is the `-sV` option which is used to get additional available information from the open ports. This method can identify versions, service names, and details about our target.

Version Scan

```shell-session
sudo nmap 10.129.59.14  -F -Pn -sV -reason 
```


`-sU`|Performs a UDP scan.|

`-sV` Performs TCP scan.`

|`-F`|Scans top 100 ports.|



 `Nmap` can save the results in 3 different formats.

- Normal output (`-oN`) with the `.nmap` file extension
- Grepable output (`-oG`) with the `.gnmap` file extension
- XML output (`-oX`) with the `.xml` file extension

We can also specify the option (`-oA`) to save the results in all formats. The command could look like this:

XML Output

```shell-session
ii001andresii@htb[/htb]$ xsltproc target.xml -o target.html
```


|   |   |
|---|---|
|`-p-`|Scans all ports.|
|`-sV`|Performs service version detection on specified ports.|



|**Scanning Options**|**Description**|
|---|---|
|`10.129.2.28`|Scans the specified target.|
|`-p 50000`|Scans only the specified ports.|
|`-sS`|Performs SYN scan on specified ports.|
|`-Pn`|Disables ICMP Echo requests.|
|`-n`|Disables DNS resolution.|
|`--disable-arp-ping`|Disables ARP ping.|
|`--packet-trace`|Shows all packets sent and received.|
|`--source-port 53`|Performs the scans from specified source port.|


## Login Brute Forcing  

```shell-session
ii001andresii@htb[/htb]$ hydra -L bill.txt -P william.txt -u -f ssh://178.35.49.134:22 -t 4
```


```shell-session
hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1
```

```
```
```
```hydra -L /usr/share/wordlists/seclists/Usernames/Names/names.txt -P /usr/share/wordlists/rockyou.txt -  
u -f 94.237.56.76 -s 31335 http-get /
```

```
## CUPP

Many tools can create a custom password wordlist based on certain information. The tool we will be using is `cupp`, which is pre-installed in your PwnBox. If we are doing the exercise from our own VM, we can install it with `sudo apt install cupp` or clone it from the [Github repository](https://github.com/Mebus/cupp). `Cupp` is very easy to use. We run it in interactive mode by specifying the `-i` argument, and answer the questions, as follows:


## Custom Username Wordlist

We should also consider creating a personalized username wordlist based on the person's available details. For example, the person's username could be `b.gates` or `gates` or `bill`, and many other potential variations. There are several methods to create the list of potential usernames, the most basic of which is simply writing it manually.

One such tool we can use is [Username Anarchy](https://github.com/urbanadventurer/username-anarchy), which we can clone from GitHub, as follows:
Code: bash

```bash
./username-anarchy Bill Gates > bill.txt
```

This tool has many use cases that we can take advantage of to create advanced lists of potential usernames. However, for our simply use case, we can simply run it and provide the first/last names as arguments, and forward the output into a file, as follows:


Hydra from login 
``hydra -L /usr/share/wordlists/seclists/Usernames/top-usernames-shortlist.txt -P /usr/share/wordlists/seclists/Passwords/Leaked-Databases/rockyou-10.txt -u 94.237.56.76 -s 31335 http-post-form  "/admin_login.php:user=^USER^&pass=^PASS^:F=<form name='log-in'"`` 


su - <user>  login with other user 



```
ffuf (FUZZ is the dinamic $i)
ii001andresii@htb[/htb]$ ffuf -w /opt/useful/SecLists/Disc
overy/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/blog/FUZZ.php
```


```shell-session
ii001andresii@htb[/htb]$ ffuf -w /opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt:FUZZ <SNIP>
```