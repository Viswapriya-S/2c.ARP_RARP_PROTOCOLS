# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
Client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter Logical Address (IP): ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

Server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("ARP Server is listening on port 8000...")
c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    print(f"Received IP: {ip}")
    mac = address.get(ip, "Not Found")
    c.send(mac.encode())
```
## OUPUT - ARP
client

<img width="817" height="325" alt="Screenshot 2026-02-02 211736" src="https://github.com/user-attachments/assets/bdfa6510-dbd0-48a6-8fc6-e2a827b5caa7" />

Server

<img width="822" height="326" alt="Screenshot 2026-02-02 212227" src="https://github.com/user-attachments/assets/e97ef136-d471-46f4-b37b-b9b5cad1a6e8" />

## PROGRAM - RARP
Server

## OUPUT -RARP
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
