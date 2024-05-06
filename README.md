# 2c.SIMULATING ARP /RARP PROTOCOLS

## NAME: SAIGURUCHANDRAN
## REG NO: 212223240143
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

## PROGRAM - ARP
## Client Program:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())    
```
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUTPUT - ARP

## CLIENT:
![WhatsApp Image 2024-05-06 at 14 20 40_1f983209](https://github.com/Saiguruchandran/2c.ARP_RARP_PROTOCOLS/assets/144870946/d5b91c5d-f3a9-467d-8d82-24604f087252)

## SERVER:
![WhatsApp Image 2024-05-06 at 14 20 51_85c0cf9d](https://github.com/Saiguruchandran/2c.ARP_RARP_PROTOCOLS/assets/144870946/13b4f2b8-2156-4364-b0e8-3cfd31998e8f)

## PROGRAM - RARP
## Client Progam:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not found".encode())    
```
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter mac address: ")
    s.send(ip.encode())
    print("Logical address",s.recv(1024).decode())
```
## OUTPUT -RARP

## CLIENT:
![WhatsApp Image 2024-05-06 at 14 21 17_a6621c5c](https://github.com/Saiguruchandran/2c.ARP_RARP_PROTOCOLS/assets/144870946/d290a705-7c18-43c1-ae2d-6c6392a0d4ae)

## SERVER
![WhatsApp Image 2024-05-06 at 14 21 26_88b7d96e](https://github.com/Saiguruchandran/2c.ARP_RARP_PROTOCOLS/assets/144870946/6de5c060-316a-4cfe-bb63-72e922c3f201)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
