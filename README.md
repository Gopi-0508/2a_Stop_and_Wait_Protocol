# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## Date: 05.02.2026
## Roll.no: 212225230084
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

server.py:

```
import socket

s = socket.socket()
s.bind(('localhost', 1234))
s.listen(1)

print("Server started, waiting for client...")
conn, addr = s.accept()
print("Connected with", addr)

while True:
    frame = conn.recv(1024).decode()
    if frame == "END":
        print("Transmission completed")
        break

    print("Frame received:", frame)
    conn.send("ACK".encode())

conn.close()
s.close()
```

client.py:

```
import socket

c = socket.socket()
c.connect(('localhost', 1234))

frame_size = int(input("Enter number of frames: "))

for i in range(frame_size):
    frame = f"Frame {i+1}"
    print("Sending:", frame)
    c.send(frame.encode())

    ack = c.recv(1024).decode()
    print("Received:", ack)

c.send("END".encode())
c.close()
```
## OUTPUT

server.py:

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a006e573-cbe5-4a9a-aa2c-09c6ee6a2473" />


client.py:

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f2ca2b59-6dd8-4e43-b237-19c3577f0db7" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
