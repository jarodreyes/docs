# Using PubNub With KONA

![alt tag](http://www.pubnub.com/static/images/structure/pubnub.png)

# Introduction

Build and Scale Realtime Apps for Connected Devices.

# Usage

From KONA you wil be the publisher in the real time game, Pubnub have more than 60 SDK to add to your client and be the subscriber.

read more at http://pubnub.com

Create your PubNub account and get the publisher key and subcriber key, here

![alt tag](http://i.imgur.com/rjRGpwI.png)

for example

```
publish key = pub-c-7529d05b-cfeb-461b-91e8-c107047c4122
```
and

```
suscribe key = sub-c-fcd1e20e-7b11-11e4-b908-02ee2ddab7fe
```

Go to KONA -> SERVICES -> PUBNUB and setup the credentials

![alt tag](http://i.imgur.com/HX2JEoe.png)

Copy the Code sample and test it!

```js
var test = function(){
    var pubnub = kona.pubnub.open('p1'); 
    
    //send the data
    pubnub.send('my_channel',"hi from kona");
};
```

Then in your account (PubNub) go to the Dev Console to see in real time the data published

![alt tag](http://i.imgur.com/NNtMaik.png)




