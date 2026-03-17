# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## Program
##server:

```
import socket

dns_table = {
    "google.com": "142.250.190.78",
    "yahoo.com": "98.137.11.163",
    "openai.com": "104.18.12.123",
    "example.com": "93.184.216.34"
}

server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

server_socket.bind(("127.0.0.1", 15353))

print("DNS Server running on port 5353...\n")

while True:
    message, client_address = server_socket.recvfrom(1024)
    domain = message.decode()
    print("Request received for:", domain)
    ip = dns_table.get(domain, "Domain not found")
    server_socket.sendto(ip.encode(), client_address)
```
## Client
```
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_address = ("127.0.0.1", 15353)

domain = input("Enter domain name: ")

# Send request to server
client_socket.sendto(domain.encode(), server_address)

ip_address, server = client_socket.recvfrom(1024)

print("IP Address:", ip_address.decode())

client_socket.close()
```
## Traceroute
```
import subprocess

def run_tracert(host):
    cmd = ['tracert', host]
    p = subprocess.Popen(cmd, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)

    for line in p.stdout:
        print(line.strip())

if __name__ == '__main__':
    run_tracert('www.google.com')
```
## Output
Server:
<img width="917" height="880" alt="Screenshot 2026-03-14 093444" src="https://github.com/user-attachments/assets/b10265ce-c45e-48bb-b7f2-e9610fb615d1" />
Client:
<img width="954" height="846" alt="Screenshot 2026-03-14 093514" src="https://github.com/user-attachments/assets/f204aeda-b9c4-4c84-a8e5-4ea07e55b51a" />
Traceoute:
<img width="875" height="733" alt="Screenshot 2026-03-14 093554" src="https://github.com/user-attachments/assets/838e795c-6119-43f3-b3dd-ba5df250ae7c" />

## Result
Thus Execution of Network commands Performed 
