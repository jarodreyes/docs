#Using SendGrid with KONA

SendGrid provides a cloud-based email delivery service that assists businesses with transactional email management while abiding by anti-spam regulations

Create an account https://sendgrid.com/ and get

```
username
```
and

```
password
```

Then just go to KONA -> Services -> Sendgrid and create it.

![alt tag](http://i.imgur.com/YtpurML.png)

```js
var test = function(){
    var sendgrid = kona.sendgrid.open("send1");

    var email = {
    	to : "some@gmail.com", from : "info@yourcompany.io",
    	fromName : "Your Company", subject : "Subject",
    	text : "Hi from <b>KONA</b>"
    }
    sendgrid.send(email);
};
```

With Sendgrid you can send emails with the from with your company domain, read more at https://sendgrid.com/docs

