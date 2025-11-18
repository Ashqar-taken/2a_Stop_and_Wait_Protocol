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
**Server**
```
import socket
Host, Port = '127.0.0.1', 62000
with socket.create_server((Host,Port)) as server:
    conn, addr = server.accept()
    print(f"Connected By: {addr}")
    while True:
        D = conn.recv(1024).decode()
        print(f"Received: {D}")
        conn.send("Received".encode())

```
**Client**
```
import socket
Host, Port = '127.0.0.1', 62000
with socket.socket(socket.AF_INET,socket.SOCK_STREAM) as client:
    client.connect((Host,Port))
    while True:
        D = input("Enter data: ")
        client.send(D.encode())
        ack = client.recv(1024).decode()
        if ack:
            print(f"Acknowledgment Received: {ack}")
            continue
        else:
            client.close()
            break
```

## OUTPUT

<img width="1595" height="1069" alt="image" src="https://github.com/user-attachments/assets/10921084-4e57-4e79-a78d-507da514c2d9" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
