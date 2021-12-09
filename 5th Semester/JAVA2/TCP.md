### Server
```java
 try (ServerSocket serverSocket = new ServerSocket(PORT)) {
 System.err.println("Server listening on port: " + serverSocket.getLocalPort());
 while (true) {
 Socket clientSocket = serverSocket.accept();
 System.err.println("Client connected from port:  " + clientSocket.getPort());
 new Thread(() -> sendExternalizableRequest(clientSocket)).start();
 }
 } catch (IOException ex) {

 Logger.getLogger(Server.class.getName()).log(Level.SEVERE, null, ex);

 }

 }
 ```