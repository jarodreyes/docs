
#Using Twilio with KONA

# Introduction

Twilio - Text Messaging, VoIP in the Cloud
Build SMS & VoIP applications via a web API using the standard web languages you already know. Start now with a free trial.
Read more at https://www.twilio.com/

First create your Twilio account, then just get the following information

![alt tag](http://i.imgur.com/sfxpOMn.png)

ACCOUNT SID
```
AC8560aba82f448f9727c1db47ffb29137
```

AUTH TOKEN
```
478c303fa1f9daa694a8c98444b73d8b
```

Then add this data to the KONA Services

![alt tag](http://i.imgur.com/lUnpXtd.png)

## Sending SMS

- First check out your account number here https://www.twilio.com/user/account/phone-numbers/incoming you must use this number in the ```FROM``` parameter.
- Before sending the sms message you must check the permision location here https://www.twilio.com/user/account/settings/international/sms, for example allows that the sms can be from Brazil.

Just copy the code and test it!

```js
//open 
var twilio = kona.twilio.open('tw1');

// send a sms
twilio.sendSMS('(FROM) Number', '(TO) Number', "This is a test message!");
```

## Sending VoIP
