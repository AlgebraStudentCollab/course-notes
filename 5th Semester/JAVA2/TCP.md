### Server
```java
try (ServerSocket serverSocket = new ServerSocket(PORT)) {
	System.err.println("Server listening on port: " + serverSocket.getLocalPort());
	while (true) {
		Socket clientSocket = serverSocket.accept();
		System.err.println("Client connected from port:  " + clientSocket.getPort());
		new Thread(() -> /* do something with the clientSocket */ ).start();
	}
} catch (...) {
	...
}
 ```
 
 ### Client
 ```java
try (Socket clientSocket = new Socket(Server.HOST, Server.PORT)) {
	System.err.println("Client connecting onto: " + clientSocket.getInetAddress() + ":" + clientSocket.getPort());
	// do something with the clientSocket
} catch ( ... ) {
	...
}
```

### Sending and receiving data
```java
DataInputStream dis = new DataInputStream(clientSocket.getInputStream());
DataOutputStream dos = new DataOutputStream(clientSocket.getOutputStream());

dos.writeUTF( ... )
oos.writeObject( ... )

...

ObjectOutputStream oos = new ObjectOutputStream(clientSocket.getOutputStream());
ObjectInputStream ois = new ObjectInputStream(clientSocket.getInputStream());

dis.readUTF( ... );
ois.readObject( ... );
 ```
 
 ### Constants
 ```java
public static final int PORT = 12345;
public static final String HOST = "localhost";
 ```