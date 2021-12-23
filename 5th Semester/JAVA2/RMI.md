## Service
Any RMI service must extend `Remote` and all methods must throw `RemoteException`
```java
public interface RemoteService extends Remote {
	
	int countConsonants(String sentence) throws RemoteException;
	String swapCharacters(String sentence) throws RemoteException;
}
```
