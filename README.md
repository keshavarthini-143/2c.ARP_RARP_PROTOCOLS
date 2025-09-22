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
```python
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
Server
```python
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode()) 

```

## OUPUT - ARP


<img width="588" height="185" alt="image" src="https://github.com/user-attachments/assets/3e2f5575-6a19-4759-9681-cdd208b0e788" />.

<img width="606" height="285" alt="image" src="https://github.com/user-attachments/assets/fe974c1e-a70b-495c-99a3-5a122214d6e1" />


## PROGRAM - RARP

Client
```python
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

Server
```python
 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP


<img width="607" height="112" alt="image" src="https://github.com/user-attachments/assets/4f0a215f-68b2-4e1c-95e5-e733d2bf61f0" />.

<img width="582" height="302" alt="image" src="https://github.com/user-attachments/assets/50d3b2f5-2a86-44d8-8ae4-d3e936d3b1e7" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
