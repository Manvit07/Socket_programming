# Socket_programming

client 

import socket

# Create a socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Server address and port
host = '127.0.0.1'  # localhost
port = 12345

# Connect to the server
client_socket.connect((host, port))

# Send a message to the server
message = "Hello Server!"
client_socket.send(message.encode())

# Receive a response from the server
data = client_socket.recv(1024).decode()
print(f"Received from server: {data}")

# Close the connection
client_socket.close()

server 

import socket

# Create a socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Host and Port
host = '127.0.0.1'  # localhost
port = 12345

# Bind the socket to the host and port
server_socket.bind((host, port))

# Start listening for connections (max 1 connection in queue)
server_socket.listen(1)
print(f"Server is listening on {host}:{port}")

# Accept the connection
conn, addr = server_socket.accept()
print(f"Connected by {addr}")

# Receive message from client
data = conn.recv(1024).decode()
print(f"Received from client: {data}")

# Send a response back to the client
response = "Hello Client, I received your message!"
conn.send(response.encode())

# Close the connection
conn.close()
