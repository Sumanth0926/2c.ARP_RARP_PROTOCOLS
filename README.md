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
## PROGRAM - ARP
### server.py
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
### client.py
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
 clinet.py

 ![Screenshot 2025-05-14 151135](https://github.com/user-attachments/assets/e121d7bd-32ed-474c-b100-4fa0d54aaeca)

 server.py

 ![Screenshot 2025-05-14 151140](https://github.com/user-attachments/assets/38514256-0d88-4cb6-a39b-e59881b987d7)


## PROGRAM - RARP
### server.py
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    mac=c.recv(1024).decode()
    try:
        c.send(address[mac].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### client.py
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac=input("Enter logical address: ")
    s.send(mac.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - RARP

client.py

![Screenshot 2025-05-14 151250](https://github.com/user-attachments/assets/a2bc8825-d95f-4153-ad48-d98f7294fd22)

server.py

![Screenshot 2025-05-14 151256](https://github.com/user-attachments/assets/e7ed1e0b-21aa-4466-9a7f-6871f81a39fd)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully executed.
