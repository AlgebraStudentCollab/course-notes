#### Assignment
Start reading:
`Jemerov D., Isakova S., Kotlin in Action, Manning 2017` [download](http://libgen.li/)


### Java compilation on android
First concept
.java -> .class .jar -> JRE \[Java Runtime Environment](proprietary)

Not using oracle proprietary runtime
.java -> .class .jar -> .dex (dalvik executable) -> apk
apk -> .dex -> DalvikVM

Optimized for battery life
apk -> .dex -> .elf -> ART \[Android Runtime Environment]

JIT compilers:
- JRE
- DalvikVM
- ART

### Android app structure
Activity - A logical group of business logic and UI	
Intent - A component separating Activities
Service - A background activity that handles time sensitive tasks
Broadcast Receiver - A listener that responds to system events
Content Provider - A public URI hosting application data for other applications to use