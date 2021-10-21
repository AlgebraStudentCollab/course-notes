## ArrayAdapter.getView(...)
method is called for every item in list
it fetched the item
inflates the template with item data
and returns the view
```kotlin
override fun getView(position: Int, convertView: View?, parent: ViewGroup): View {  
  
    return super.getView(position, convertView, parent)  
}
```


- position - item position
- 