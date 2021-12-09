### Server
```java
try (ServerSocket serverSocket = new ServerSocket(PORT)) {
	System.err.println("Server listening on port: " + serverSocket.getLocalPort());
	while (true) {
		Socket clientSocket = serverSocket.accept();
		System.err.println("Client connected from port:  " + clientSocket.getPort());
		new Thread(() -> /* do something with the clientSocket */ ).start();
	}
} catch (IOException ex) {
...
}
 ```
 
 ### Client
 ```java
try (Socket clientSocket = new Socket(Server.HOST, Server.PORT)) {
	System.err.println("Client connecting onto: " + clientSocket.getInetAddress() + ":" + clientSocket.getPort());
	// do something with the clientSocket
} catch (IOException | ClassNotFoundException ex) {
	Logger.getLogger(Client.class.getName()).log(Level.SEVERE, null, ex);
}
```

### Sending and receiving data
```java
DataInputStream dis = new DataInputStream(clientSocket.getInputStream());
DataOutputStream dos = new DataOutputStream(clientSocket.getOutputStream());

dos.writeUTF()
 ```