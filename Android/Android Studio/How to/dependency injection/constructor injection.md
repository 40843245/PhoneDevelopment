# constructor injection
## How to constructor injection in Android Studio
Do depenedency injection at constructor.

See the following example.

```
class Engine constructor(name : String){
  lateinit var name : String
  init{
    this.name = name
  }

}
class Car constructor(engine:Engine){
  lateinit var engine:Engine
  init{
     this.engine = engine;
  }      
    
fun main(){
  var car:Car = Car(Engine)
}
```

## What things one can't do constructor injection?

+ an interface
+ a type that you do not own, such as a class from an external library.

**However**

In these cases, you can provide Hilt with binding information by using Hilt modules.
