# RMI
Implemented using [[JNDI]]
## Service
Any RMI service must extend `Remote` and all methods must throw `RemoteException`
```java
public interface RemoteService extends Remote {
	String REMOT_OBJECT_NAME = "hr.algebra.rmi.remoteservice";
	int countConsonants(String sentence) throws RemoteException;
	String swapCharacters(String sentence, char oldChar, char newChar) throws RemoteException;
}
```

