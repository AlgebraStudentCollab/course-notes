# RMI
Implemented using [[JNDI]]
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

All method 