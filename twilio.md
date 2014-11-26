
#Using Twilio with KONA

# Introduction

Twilio - Text Messaging, VoIP in the Cloud
Build SMS & VoIP applications via a web API using the standard web languages you already know. Start now with a free trial.
Read more at https://www.twilio.com/

First create your Twilio account, then just get the following information

![alt tag](http://i.imgur.com/TLlmD9o.png)

ACCOUNT SID
```
AC8560aba82f448f9727c1db47ffb29137
```

AUTH TOKEN
```
478c303fa1f9daa694a8c98444b73d8b
```

Then add this data to the KONA Services, go to Services (or Connectors) and then choose Twilio Service

![Imgur](http://i.imgur.com/kSSpz4pl.png)

- First check out your account number here https://www.twilio.com/user/account/phone-numbers/incoming you must use this number in the ```FROM``` parameter.

## Sending SMS

- Before sending the sms message you must check the permision location here https://www.twilio.com/user/account/settings/international/sms, for example allows that the sms can be from Brazil.

Just copy the code and test it!

```js
//open 
var twilio = kona.twilio.open('tw1');
// send a sms
twilio.sendSMS('(FROM) Number', '(TO) Number', "This is a test message!");
```

## Sending VoIP

- Before sending the voIP call you must check that your country is supported, for example Uruguay it's not supported right row.

```js
//open 
var twilio = kona.twilio.open('tw1');
// send a sms
twilio.sendVoIP('(FROM) Number', '(TO) Number', "http://demo.twilio.com/welcome/voice/");
```

You can change the URL for the text, more information in twilio documentation
