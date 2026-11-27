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
server:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind(('localhost', 8000))
s.listen(1)

print("Server waiting for connection...")

c, addr = s.accept()

print("Client connected:", addr)

while True:
    msg = c.recv(1024).decode()

    if msg.lower() == "exit":
        print("Client disconnected")
        break

    print("Client:", msg)

    reply = input("Server: ")
    c.send(reply.encode())

    if reply.lower() == "exit":
        break

c.close()
s.close()
```
client:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(('localhost', 8000))

print("Connected to server")

while True:
    msg = input("Client: ")

    s.send(msg.encode())

    if msg.lower() == "exit":
        break

    reply = s.recv(1024).decode()

    if reply.lower() == "exit":
        print("Server disconnected")
        break

    print("Server:", reply)

s.close()
```
## OUPUT
<img width="1347" height="355" alt="image" src="https://github.com/user-attachments/assets/76b1d693-d243-430a-9d81-21c9de5dfa02" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
