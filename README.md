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
SERVER:
```
import socket

s = socket.socket()
s.bind(('localhost', 9999))
s.listen(1)

while True:
    c, addr = s.accept()
    print('Connection Established')
    print('Connected by', addr)
    while True:
        content=c.recv(1024).decode()
        if not content:
            break
        with open('received_file.txt', 'w') as f:
            f.write(content)
        print('File received and saved as received_file.txt')
        c.send('File received successfully'.encode())
    c.close()
```

CLIENT:
~~~
import socket

c= socket.socket()
c.connect(('localhost', 9999))
while True:
    filename = input('Enter the file name: ')
    if not filename:
        break   
    with open(filename, 'r') as f:
        content=f.read()

    c.send(content.encode())
    print('File sent successfully')
    response = c.recv(1024).decode()
    if not response:
        print('File not received by server\n')
    else:
        print("File received by server successfully\n")
c.close()
~~~

## OUPUT

<img width="1917" height="1021" alt="image" src="https://github.com/user-attachments/assets/c61e9c39-86eb-42ca-800f-675b2eab7b8f" />

<img width="1918" height="1021" alt="image" src="https://github.com/user-attachments/assets/300350d4-0472-4c4b-b854-940f7878975a" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
