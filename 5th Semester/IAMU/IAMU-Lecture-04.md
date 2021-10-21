## Viewbinding in Gradle
```gradle
buildFeatures() {  
 viewBinding true  
}
```

Gradle generates 

.java -> .class -> .dex

## Using the tools namespace
The namespace has to be included in the root element
```xml
...
xmlns:tools="http://schemas.android.com/tools"
...
```