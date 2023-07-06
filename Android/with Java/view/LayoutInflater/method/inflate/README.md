# LayoutInflater.inflate
## intro
Inflate a new view hierarchy from the specified xml node.

## syntax

    inflate(int resource, ViewGroup root)

    inflate(XmlPullParser parser, ViewGroup root)

    inflate(int resource, ViewGroup root, boolean attachToRoot)

    inflate(XmlPullParser parser, ViewGroup root, boolean attachToRoot)

### parameter
I will list them together.

      resource : a resource layout ID in xml file.

      parser : XML DOM node.

      root : Optional view to be the parent of the generated hierarchy. It may be null.

      attachToRoot : A boolean value whether the inflated hierarchy should be attached to the optional view (in parameter root).

                     If true, it will be attached. 

                     If false, the optional view is only used to create correct subclass of LayoutParams for root view in the XML.
## Example 
### Example 1
#### Code
    View view_1 ;
    view_1 = LayoutInflater.from(getApplication()).inflate(R.layout.view_1, null);
#### Screenshot
![image](https://github.com/40843245/PhoneDevelopment/assets/75050655/21e15d94-0164-44dc-bcb6-a8dff0b5cf57)

The part of structure of the project.

#### Explanation
We will get the root content in view_1.xml which is located in ../res/layout directory (shown in the above screenshot), then store it into the variable view_1.


## Ref
https://developer.android.com/reference/android/view/LayoutInflater#inflate(org.xmlpull.v1.XmlPullParser,%20android.view.ViewGroup,%20boolean)
