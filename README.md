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

    client.py
    import socket
    s=socket.socket()
    s.bind(('localhost',8000))
    s.listen(5)
    c,addr=s.accept()
    address={"172.18.82.127":"E0:2E:0B:7B:0D:8B","165.165.79.1":"8A:BC:E3:FA"};
    while True:
    ip=c.recv(1024).decode()
    try:
    c.send(address[ip].encode())
    except KeyError:
    c.send("Not Found".encode())
    import socket
    s=socket.socket()
    s.connect(('localhost',8000))
    while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

    
## OUPUT - ARP

##client


![Screenshot 2025-04-26 104833](https://github.com/user-attachments/assets/c87dccf5-127f-45f1-abc5-2f67353d8381)

##server

![Screenshot 2025-04-26 104840](https://github.com/user-attachments/assets/1eb77545-a742-4c69-9e97-9b6e8740f5ae)



## PROGRAM - RARP

    client.py
    import socket
    s=socket.socket()
    s.bind(('localhost',9000))
    s.listen(5)
    c,addr=s.accept()
    address={"E0:2E:0B:7B:0D:8B":"172.18.82.127","8A:BC:E3:FA":"192.168.1.99"};
    while True:
    ip=c.recv(1024).decode()
    try:
    c.send(address[ip].encode())
    except KeyError:
    c.send("Not Found".encode())
    import socket
    s=socket.socket()
    s.connect(('localhost',9000))
    while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
    

## OUPUT -RARP

##client

![Screenshot 2025-04-26 105040](https://github.com/user-attachments/assets/e52b6272-3c2e-4b56-b309-2822ef78576a)

##server

![Screenshot 2025-04-26 105048](https://github.com/user-attachments/assets/e00580b0-dcea-49ac-a6b2-63fe4182a56f)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
