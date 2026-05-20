4.Execution_of_NetworkCommands

AIM :Use of Network commands in Real Time environment

Software : Command Prompt And Network Protocol Analyzer

Procedure: To do this EXPERIMENT- follows these steps:

In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer
All commands related to Network configuration which includes how to switch to privilege mode
and normal mode and how to configure router interface and how to save this configuration to
flash memory or permanent memory.
This commands includes
• Configuring the Router commands
• General Commands to configure network
• Privileged Mode commands of a router
• Router Processes & Statistics
• IP Commands
• Other IP Commands e.g. show ip route etc.

Program:
server.py
```python
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000)) 
s.listen(5)
print("Ping Server is listening on port 8000...")

c, addr = s.accept()
print(f"Connected to client: {addr}")

while True:
    hostname = c.recv(1024).decode()
    if not hostname:
        break
        
    print(f"Client requested ping for: {hostname}")
    
    try:
        result = ping(hostname, verbose=False)
        response_text = f"\n{result}"
        c.send(response_text.encode())
        
    except Exception as e:
        error_msg = f"Error: Could not ping '{hostname}'. ({str(e)})"
        c.send(error_msg.encode())

c.close()
s.close()
print("Server shut down.")
```
client.py
```python
import socket

# Initialize the Client
s = socket.socket()
s.connect(('localhost', 8000))
print("Connected to the Ping Server. (Type 'exit' to quit)\n")

while True:
    ip = input("Enter the website you want to ping: ")
    
    if ip.lower() == 'exit' or not ip:
        break
        
    # Send the website name to the server
    s.send(ip.encode())
    
    # Receive and print the ping report from the server
    print("\n--- Ping Results From Server ---")
    print(s.recv(4096).decode())  # Buffer size bumped to 4096 to fit entire ping reports
    print("-" * 32 + "\n")

s.close()
print("Client disconnected.")
```
Output
server:
<img width="984" height="255" alt="Screenshot (483)" src="https://github.com/user-attachments/assets/869f6063-95e4-452a-bb1d-5e7476d758b9" />
client:
<img width="955" height="462" alt="Screenshot (484)" src="https://github.com/user-attachments/assets/fe23d0ad-f970-4b04-9dee-4a1d01704740" />


Result

Thus Execution of Network commands Performed
