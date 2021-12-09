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

  

 for (int j = 0; j < 3; j++) {

 byte[] buffer = new byte[64];

 DatagramPacket packet = new DatagramPacket(buffer, buffer.length);

 clientSocket.receive(packet);
String message = new String(packet.getData(), 0, packet.getLength());
System.out.println(message);
}
System.err.println("Client left:" + getName());
clientSocket.leaveGroup(groupAddress);
} catch (IOException ex) {
}
 ```

### Sending and receiving data

### Constants
```java
public static final int PORT = 4446;
public static final String GROUP = "230.0.0.1";
 ```