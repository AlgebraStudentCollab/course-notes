# ClassLoader
loads classes into the JVM
1. Bootstrap ClassLoader
	- Written natively in C
	- Loaded directly by the JVM
2. Extension (Platform) ClassLoader
	- Loads classes defined in `java.ext.dirs` (`$JAVA_HOME/jre/lib/ext`)
	- Bootstrap is the parent
3. Application (System) ClassLoader
	- Loads classes defined in the classpath
	- Platform is the parent