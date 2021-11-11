ClassLoaders write class
- Bootstrap ClassLoader
	- Written natively in C
	- Loaded directly by the JVM
- Extension (Platform) ClassLoader
	- Loads classes defined in `java.ext.dirs` (`$JAVA_HOME/jre/lib/ext`)
	- Bootstrap is the parent
- Application (System) ClassLoader
	- Loads classes defined in the classpath
	- Platform is the parent