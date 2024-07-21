# A model of Android app's application graph 

![image](https://github.com/user-attachments/assets/37c65dcb-0651-4331-ace9-8ae6224e0429)

In the above figure, each `Activity`/`Fragment` has one `ViewModel` which contains lots of `LiveData`. 

Additionally, each `ViewModel` has one `Repository`. 

Each `Reposity` has one `Model` and `Remote Data source`.

Each `Model` contains one `Room` that has one [`SQLite`](https://en.wikipedia.org/wiki/SQLite) (which is a kind of database engine.)

Each `Remote Data source` contains one `Retrofit` that has one [`webservice`](https://en.wikipedia.org/wiki/Web_service) (which is a service that communicates from an electronic device to another via the Internet,)

## Ref

For more details, see [A model of Android app's application graph](https://developer.android.com/training/dependency-injection/manual)

