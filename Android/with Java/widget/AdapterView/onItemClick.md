# onItemClick -- The event function to be invoked for click of items or saying when setOnItemClickListener is called.
## intro 
It is an abstract method about setOnItemClickListener event callback function. Since it is abstract, you must override it instead of directly invoking it.

It is usually used in setOnItemClickListener.

For more fully understanding and usage, see syntax and the following example.

## syntax
    public abstract void onItemClick (AdapterView<?> parent, 
                View view, 
                int position, 
                long id)
### parameter
      
 In 
 
                public abstract void onItemClick (AdapterView<?> parentView, 
                View view, 
                int position, 
                long id)
                
      
                parentView : The parent of the selected item. It must be the AdapterView instance or instance of its subclass.
                
                view : The view within the instance parentView. It must be the AdapterView instance or instance of its subclass.
                
                position : The index of selected item. You can access the selected item with the parameter and getItemAtPosition method.
                
                For more details and usage of the getItemAtPosition, see my other post.
                
                https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/AdapterView/getItemAtPosition.md
                
                id : The row id of the item that was clicked.
  
## Example

In the project in the zip file.

https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/AdapterView/zip/project/getItemAtPosition_1.zip

## Ref
https://github.com/40843245/PhoneDevelopment/blob/main/Android/with%20Java/widget/AdapterView/zip/project/getItemAtPosition_1.zip



