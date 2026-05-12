# 2c.SIMULATING ARP /RARP PROTOCOLS
## DATE:12/05/2026
## NAME:BRINDHA A R
## REG:212225040050
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
## CLIENT SIDE
```
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening on port 8001...")
c, addr = s.accept()

address = {
    "FC:6D:77:6C:71:5E": "10.228.26.27",
    "8A:BC:E3:FA": "165.165.79.1"
}
```
## SERVER SIDE
```
import socket

s = socket.socket()
s.connect(('localhost', 8001))

while True:
    mac = input("Enter Physical Address (MAC): ")
    s.send(mac.encode())
    print("IP Address:", s.recv(1024).decode())

while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())
```

## OUPUT - ARP
<img width="1919" height="567" alt="Screenshot 2026-05-12 130838" src="https://github.com/user-attachments/assets/82e5043e-f68f-47ff-8e7e-bd5718f5ba5d" />

## PROGRAM - RARP

## CLIENT SIDE
```
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening on port 8001...")
c, addr = s.accept()

address = {
    "FC:6D:77:6C:71:5E": "10.228.26.27",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())
```
## SERVER SIDE
```
import socket

s = socket.socket()
s.connect(('localhost', 8001))

while True:
    mac = input("Enter Physical Address (MAC): ")
    s.send(mac.encode())
    print("IP Address:", s.recv(1024).decode())
```
## OUPUT -RARP

<img width="1915" height="546" alt="Screenshot 2026-05-12 132848" src="https://github.com/user-attachments/assets/a7ae80ee-16c1-4895-baec-c2b6d7bc77de" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
