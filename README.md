# Socket_programming

client 

import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'  # localhost
port = 12345

client_socket.connect((host, port))

message = "Hello Server!"
client_socket.send(message.encode())

data = client_socket.recv(1024).decode()
print(f"Received from server: {data}")

client_socket.close()

server 

import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'  # localhost
port = 12345

server_socket.bind((host, port))

server_socket.listen(1)
print(f"Server is listening on {host}:{port}")

conn, addr = server_socket.accept()
print(f"Connected by {addr}")

data = conn.recv(1024).decode()
print(f"Received from client: {data}")

response = "Hello Client, I received your message!"
conn.send(response.encode())

conn.close()
