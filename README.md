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
<img width="1908" height="533" alt="Screenshot 2026-05-12 142114" src="https://github.com/user-attachments/assets/b6aec027-82aa-4ebd-b212-7ccfc458e826" />


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

<img width="1914" height="472" alt="Screenshot 2026-05-12 142256" src="https://github.com/user-attachments/assets/2ec401dd-fa86-476c-81cb-4ebccbcafb31" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
