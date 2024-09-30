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
### CLIENT
```
socket 
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
### SERVER
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

![Screenshot (205)](https://github.com/user-attachments/assets/3421e8e0-82b4-477b-8bc1-6d7dac182ee7)
![Screenshot (204)](https://github.com/user-attachments/assets/9214a6d1-dc9f-48cc-a1c0-6ba70fb8d8b7)

## PROGRAM - RARP
### CLIENT
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
### SERVER
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

![Screenshot (206)](https://github.com/user-attachments/assets/6afc7b68-ecfe-43d7-b3d0-2ff32f28d743)
![Screenshot (207)](https://github.com/user-attachments/assets/deb51bd8-70ae-465d-ab86-5f1596cd2ded)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
