### Server
```java
try (DatagramSocket serverSocket = new DatagramSocket()) {
	while (true) {
		String message = ...
		byte[] buffer = message.getBytes();
		InetAddress groupAddress = InetAddress.getByName(GROUP);
		DatagramPacket packet = new DatagramPacket(buffer, buffer.length, groupAddress, PORT);
		serverSocket.send(packet);
	}
} catch ( ... ) {
	...
}
 ```

### Client
```java
try (MulticastSocket clientSocket = new MulticastSocket(Server.PORT)) {
	InetAddress groupAddress = InetAddress.getByName(Server.GROUP);
	System.err.println("Client joining:" + getName());
	clientSocket.joinGroup(groupAddress);
	
	// do something with clientSocket
	
	System.err.println("Client left:" + getName());
	clientSocket.leaveGroup(groupAddress);
} catch ( ... ) {
	...
}
 ```

### Sending and receiving data
#### Sending
#### 
```java
for (int j = 0; j < 3; j++) { // read 3 messages before leaving the group
		byte[] buffer = new byte[64]; // create a bytebuffer to store the message in
		DatagramPacket packet = new DatagramPacket(buffer, buffer.length); // wrap it in a datagrampacket
		clientSocket.receive(packet); // wait for new messages
		String message = new String(packet.getData(), 0, packet.getLength()); // 
		System.out.println(message);
	}
```
### Constants
```java
public static final int PORT = 4446;
public static final String GROUP = "230.0.0.1";
 ```