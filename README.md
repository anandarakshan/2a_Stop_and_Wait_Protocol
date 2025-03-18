# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### Server.py
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
while True:
    i = input("Enter a data: ")
    c.send(i.encode())  
    ack = c.recv(1024).decode()  
    if ack:
        print(ack)  
        continue
    else:
        c.close()   
        break
```
### client.py
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print("Received from Server:", data)
    s.send("Acknowledgement Received".encode())
s.close()
```
## OUTPUT
![alt text](<Screenshot 2025-03-18 112950.png>)
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
