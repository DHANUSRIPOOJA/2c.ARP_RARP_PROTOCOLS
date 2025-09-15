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
# CLIENT
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
# Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
# Client
<img width="941" height="894" alt="image" src="https://github.com/user-attachments/assets/2aab565e-1ad3-434b-a32b-f663558ad174" />
# server
<img width="671" height="551" alt="image" src="https://github.com/user-attachments/assets/9b20a6c8-8df2-46af-ac6e-ed8384cd5a21" />


## PROGRAM - RARP
# Client
```
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
```
# server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
# Client
<img width="675" height="488" alt="image" src="https://github.com/user-attachments/assets/5d9fa78a-c8cf-48d3-b85e-c7da94ce74a1" />

# Server
<img width="939" height="796" alt="image" src="https://github.com/user-attachments/assets/bc8aa935-01a1-4405-aea5-8dcdbe511fff" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
