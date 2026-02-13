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
Server Side
```py
import socket
print("SERVER FILE STARTED")

port = 60000
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(5)

print("Server is running...")
print("Waiting for client connection...")

while True:
    conn, addr = s.accept()
    print("Connected to:", addr)

    data = conn.recv(1024)
    print("Server received:", data.decode())

    with open("mytext.txt", "rb") as f:
        while True:
            chunk = f.read(1024)
            if not chunk:
                break
            conn.send(chunk)

    print("Done sending file")
    conn.send(b"\nThank you for connecting")
    conn.close()
```
Client Side
```py
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('mytext.txt', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('Connection closed')
```
## OUPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/075deeca-ad28-4fd8-a4e6-1b50ec8e8de7" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
