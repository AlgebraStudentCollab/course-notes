### Server
```java
try (DatagramSocket serverSocket = new DatagramSocket()) {
while (true) {

 String message = LocalDateTime.now().format(DateTimeFormatter.ISO_DATE_TIME);

 byte[] buffer = message.getBytes();

 InetAddress groupAddress = InetAddress.getByName(GROUP);

 DatagramPacket packet = new DatagramPacket(buffer, buffer.length, groupAddress, PORT);

  

 serverSocket.send(packet);

 Thread.sleep(6000);

 }

 } catch (SocketException | UnknownHostException ex) {

 Logger.getLogger(Server.class.getName()).log(Level.SEVERE, null, ex);

 } catch (IOException ex) {

 Logger.getLogger(Server.class.getName()).log(Level.SEVERE, null, ex);

 } catch (InterruptedException ex) {

 Logger.getLogger(Server.class.getName()).log(Level.SEVERE, null, ex);

 }
 ```

### Client

### Sending and receiving data