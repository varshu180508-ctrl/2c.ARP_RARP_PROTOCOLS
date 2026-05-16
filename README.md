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
## PROGRAM - RARP

server:
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server is listening for RARP requests...")
c, addr = s.accept()
print(f"Connection established with {addr}")

rarp_table = {
    "6A:08:AA:C2": "165.165.80.80",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()
    f not mac:  
        break
        try:
        ip = rarp_table[mac]  
        print(f"MAC: {mac} -> IP: {ip}")
        c.send(ip.encode())  
    except KeyError:
        print(f"MAC: {mac} not found in RARP table.")
        c.send("Not Found".encode())
c.close()
s.close()

client:

import socket
c = socket.socket()
c.connect(('localhost', 8000))
while True:
    mac = input("Enter MAC address to find IP (or type 'exit' to quit): ")
    if mac.lower() == "exit":  
        break
    c.send(mac.encode())
    ip = c.recv(1024).decode()
    print(f"IP Address for {mac}: {ip}")
c.close()


##OUPUT 
ARP


CLIENT
<img width="1920" height="921" alt="Screenshot (164)" src="https://github.com/user-attachments/assets/40d63bd1-e66c-43f6-af61-da6f85f6f4d4" />

SERVER

<img width="1920" height="1060" alt="Screenshot (165)" src="https://github.com/user-attachments/assets/5395e689-30fa-4f30-9b50-e6dff7bc11ff" />


RARP

CLIENT

<img width="1920" height="929" alt="Screenshot (166)" src="https://github.com/user-attachments/assets/4744fe71-03ef-4eff-a72a-dda433cfe20d" />


SERVER

<img width="1920" height="893" alt="Screenshot (167)" src="https://github.com/user-attachments/assets/041584ce-97a6-48b5-ae02-84e674350eb6" />





## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
