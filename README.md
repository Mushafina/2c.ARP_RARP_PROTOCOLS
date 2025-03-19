# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME:R.MUSHAFINA 
## REGISTER NUMBER:212224220067
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
```
CLIENT
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
SERVER
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUTPUT - ARP
![Screenshot 2025-03-19 110805](https://github.com/user-attachments/assets/d2f68505-0c66-45f0-8a40-805f0c0ef0ec)
![Screenshot 2025-03-19 110736](https://github.com/user-attachments/assets/68fb8301-544f-400b-b609-672ae4279de2)

## PROGRAM - RARP
```
CLIENT
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode()) 
SERVER
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUTPUT -RARP
![Screenshot 2025-03-19 111819](https://github.com/user-attachments/assets/a6faf4bc-abe5-4445-966c-66e58c48e5d6)
![Screenshot 2025-03-19 111802](https://github.com/user-attachments/assets/d0255b80-e2a8-452c-b150-9cdfdc4a7b55)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
