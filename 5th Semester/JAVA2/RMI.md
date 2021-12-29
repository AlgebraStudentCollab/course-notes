# RMI
- Invocation of a method on a remote JVM over [[JNDI]]
- Implementation of RPC in Java
## Service (Contract)
Any RMI service must extend `Remote` and all methods must throw `RemoteException`

```java
public interface RemoteService extends Remote {
	String REMOT_OBJECT_NAME = "hr.algebra.rmi.remoteservice";
	int countConsonants(String sentence) throws RemoteException;
	String swapCharacters(String sentence, char oldChar, char newChar) throws RemoteException;
}
```

We need to know the exact class of any service that we want to access through RMI

```java
String REMOT_OBJECT_NAME = "hr.algebra.rmi.remoteservice";
```

All methods need to throw `RemoteException`'s due to the possibilty of failing the check

## Implementation
Serverside implementation of the contract, code execution happens on the JVM that exposes an instance of this object.

All data will be serialized for transport between JVMs, method parameters and return type should also be `Serializable` to allow for data transfer.

```java
public class RemoteServiceImpl implements RemoteService {

    @Override
    public int countConsonants(String sentence) throws RemoteException {
        return sentence
                .replace("[^a-zA-Z]", "")
                .replace("[^aeiou]", "")
                .length();
    }

    @Override
    public String swapCharacters(String sentence, char oldChar, char newChar) throws RemoteException {
        return sentence.replace(oldChar, newChar);
    }

}
```

## Server
```java
public class RMIServer {

	// Port on which the JVM exposes the registry that hosts an instance of this class
    private static final int RMI_PORT = 1099;
	// Notifies the JNDI API not to use dynamically assigned ports for replies
    private static final int RANDOM_PORT_HINT = 0;

    public static void main(String[] args) {
        try {
            // Exposes JVM to port: RMI_PORT
            Registry registry = LocateRegistry.createRegistry(RMI_PORT);
            // Instance of remotely available class
            RemoteService service = new RemoteServiceImpl();
            // Instance of skeleton that will deserialize remote data and call the intended method
            RemoteService skeleton = (RemoteService) UnicastRemoteObject.exportObject(service, RANDOM_PORT_HINT);
            System.err.println("Object registered in RMI Registry");
            // routes any calls to REMOTE_OBJECT_NAME to the skeleton
            registry.rebind(RemoteService.REMOTE_OBJECT_NAME, skeleton);
        } catch (RemoteException ex) {
            Logger.getLogger(RMIServer.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
}
```

## Client
```java
public class RMIClient {

    public static void main(String[] args) {
        try {
			// Locates the required registry on the hostname "localhost", on port 1099
            Registry registry = LocateRegistry.getRegistry("localhost", 1099);
			// The Stub forwards all requests bound for the RemoteService instance trough to the remote JVM
            RemoteService stub = (RemoteService) registry.lookup(RemoteService.REMOTE_OBJECT_NAME);
			// Simple method to demonstrate the service in action
            handleRemoteCalls(stub);

        } catch (RemoteException ex) {
            Logger.getLogger(RMIClient.class.getName()).log(Level.SEVERE, null, ex);
        } catch (NotBoundException ex) {
            Logger.getLogger(RMIClient.class.getName()).log(Level.SEVERE, null, ex);
        }
    }

	// Example use
    private static void handleRemoteCalls(RemoteService remoteService) throws RemoteException {
        try (Scanner scanner = new Scanner(System.in)) {
            System.out.println("Insert sentence: ");
            final String sentence = scanner.nextLine();
            int consonants = remoteService.countConsonants(sentence);
            System.out.println("Number of consonants: " + consonants);
            System.out.println("Character to change: ");
            char oldChar = scanner.next().charAt(0);
            System.out.println("Character to change to: ");
            char newChar = scanner.next().charAt(0);
            System.out.println("Sentece: " + remoteService.swapCharacters(sentence, oldChar, newChar));
        } catch (RemoteException ex) {
            Logger.getLogger(RMIClient.class.getName()).log(Level.SEVERE, null, ex);
        }
    }
}
```