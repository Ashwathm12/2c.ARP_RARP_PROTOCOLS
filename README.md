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
        c.send("NotFound".encode())

```
## OUPUT - ARP
![2cclient](https://github.com/Ashwathm12/2c.ARP_RARP_PROTOCOLS/assets/138849225/a9df947f-4a0e-4b31-97f5-eab728c347ae)

## PROGRAM - RARP
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address:")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT -RARP
![2cserver](https://github.com/Ashwathm12/2c.ARP_RARP_PROTOCOLS/assets/138849225/fe1486d6-ef02-43fe-94b9-c545d2b9fa9a)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
