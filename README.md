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

**##Program**:
client.py
```python
import socket
s = socket.socket()
host = socket.gethostname() 
port = 60000 
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True: 
        print('receiving data...') 
        data = s.recv(1024) 
        print('data=%s', (data)) 
        if not data:
            break 
        f.write(data)
        
print('Successfully get the file')
s.close()
print('connection closed')
```
server.py
```python
import socket

port = 60000
s = socket.socket()

host = socket.gethostname()

s.bind((host, port))

s.listen(5)

print("Waiting for connection...")

conn, addr = s.accept()

print("Connected by:", addr)

message = conn.recv(1024)

print("Message from client:", message.decode())

with open("sample.txt", "rb") as f:
    data = f.read()
    conn.send(data)

conn.close()
```

## Output
client:
<img width="1146" height="367" alt="Screenshot (481)" src="https://github.com/user-attachments/assets/b31b2813-44fc-4587-ba4c-b9e9bc72c075" />
server:
<img width="984" height="225" alt="Screenshot (482)" src="https://github.com/user-attachments/assets/f2d0d935-6f54-4bd3-9e5b-3e93565c5794" />

## Result
Thus Execution of Network commands Performed 
