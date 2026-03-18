# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server
```
import socket

host = '127.0.0.1'
port = 6000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)

print("Server waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to:", addr)

filename = "sample.txt"

with open("DOC.txt", "rb") as file:
    data = file.read()
    conn.send(data).encode()

print("File sent successfully")
conn.close()
server_socket.close()
```

Client
```
import socket

host = '127.0.0.1'
port = 6000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

with open("DOC1.txt", "wb") as file:
    while True:
        data = client_socket.recv(1024)
        if not data:
            break
        file.write(data)

print("File received successfully")
client_socket.close()
```
## OUPUT
Server
<img width="1433" height="64" alt="image" src="https://github.com/user-attachments/assets/2fb52947-2e0b-4e85-836d-e7ce84d45cfc" />

Client
<img width="1426" height="236" alt="image" src="https://github.com/user-attachments/assets/1e08d8e5-3cda-4316-8f2e-411b361e2acf" />

Source
<img width="740" height="647" alt="image" src="https://github.com/user-attachments/assets/18972923-b8d8-4a13-9277-b5f9fe47467b" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
