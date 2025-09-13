# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

ex2bs.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
ex2bc.py
```
import socket
s=socket.socket()
s.connect(('localhost', 8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```

## OUPUT

<img width="1471" height="731" alt="Screenshot 2025-09-13 163235" src="https://github.com/user-attachments/assets/8cb4ce99-44f7-4f07-b417-03e790704607" />


<img width="1466" height="683" alt="Screenshot 2025-09-13 163258" src="https://github.com/user-attachments/assets/857d964c-b76b-4f28-90b3-e62a5d194d4b" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
