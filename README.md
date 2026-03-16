# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software :
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:

Students have to understand basic networking commands such as:
```
•tcpdump
```
```
•netstat
```
```
•ifconfig
```
```
•nslookup
```
```
•traceroute
```

Additionally, capture ping and traceroute PDUs using a network protocol analyzer.

This includes all commands related to network configuration, such as:

• Switching to privileged mode and normal mode

• Configuring router interfaces

• Saving the configuration to flash memory or permanent memory

This commands includes

• Configuring the Router commands

• General Commands to configure network

• Privileged Mode commands of a router 

• Router Processes & Statistics

• IP Commands

• Other IP Commands e.g. show ip route etc.
## Algorithm
Algorithm: Server Ping Program

1. Start the program.
2. Import socket and pythonping modules.
3. Create a socket.
4. Bind the socket to localhost and port 8000.
5. Listen for client connections.
6. Accept the client connection.
7. Receive hostname from the client.
8. If hostname is "exit", terminate the connection.
9. Ping the received hostname.
10. Send the ping result back to the client.
11. Close the connection.
12. Stop the program.

Algorithm: Client Ping Request Program

1. Start the program.
2. Import socket module.
3. Create a socket.
4. Connect to the server at localhost port 8000.
5. Ask the user to enter a hostname or IP address.
6. Send the hostname to the server.
7. Receive the ping result from the server.
8. Display the result.
9. If user enters "exit", close the connection.
10. Stop the program.

## Program
```
Server.py
```
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
```
Client.py
```
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
## Server
<img width="1254" height="252" alt="image" src="https://github.com/user-attachments/assets/a4532ba0-ed4d-4857-ad4a-d73434c6f2bd" />


## Client

<img width="847" height="424" alt="image" src="https://github.com/user-attachments/assets/bcb330b7-a101-4904-ac59-cc9ec9745bb4" />


```
traceroute
```
<img width="826" height="475" alt="image" src="https://github.com/user-attachments/assets/ce552f95-f869-4baa-8740-39bee4cef844" />


```
ipconfig
```
<img width="983" height="770" alt="image" src="https://github.com/user-attachments/assets/41371524-54fa-429d-b530-2440620bd73e" />

```
nslookup
```
<img width="632" height="629" alt="image" src="https://github.com/user-attachments/assets/16f3e160-0477-4acc-9f30-bb24f6a5b1ec" />


```
netstat
```
<img width="735" height="880" alt="image" src="https://github.com/user-attachments/assets/23d71a7e-796e-4445-9366-e49b6ee5f820" />


```
tcpdump
```
<img width="839" height="511" alt="image" src="https://github.com/user-attachments/assets/39c7cc94-1c47-438f-be2c-212e0563e9dd" />

## Result
Thus Execution of Network commands Performed 
