#Using Loggly With KONA

#Introduction

The World’s Most Popular Cloud-Based, Enterprise-Class Log Management Solution

more info at https://www.loggly.com/why-loggly/

# Using

first create your account and get the URL, for example

```
https://logs-01.loggly.com/bulk/519e8122-5207-4413-9512-7a42e99bda12/tag/file_upload
```

Go to KONA -> Services -> Logggly and setup the URL.

![alt tag](http://i.imgur.com/Xv5eRqE.png)

In your code just log

JSON Logging

```js
var loggly = kona.loggly.open("l1");

var info = {
	some : "some"
};
loggly.log(info);
```

String Logging

```js
var loggly = kona.loggly.open("l1");
loggly.log("some string");
```

Enjoy your logs in loggly

![alt tag](http://i.imgur.com/zy38CVY.png)
