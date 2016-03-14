---
title: "How to send SMS with PHP?"
read_time: "1 min"
updated: "March 14, 2016"
group: "general"
permalink: "/faq/how-to-send-sms-with-php/"

compass:
  prev: "/faq/single-vs-double-quotes-in-php/"
  next: "/faq/templating/"
---

Sending SMS with web application can be useful for multiple purposes. For instance
you can increase security with integrate multi-factor authentication system and
increase security, retrieve forgotten passwords, send marketing messages, notify
users about different events and similar.

Diagram below explains a simplified SMS sending flow where PHP application
communicates with SMS gateway which converts and forward received data to SMS center (SMSC). SMSC
routes data to mobile device (end user).

![Sending SMS with PHP](/images/faq/general/sms.png "Sending SMS with PHP")

## See also

* [gnokii](https://www.gnokii.org/) - Allows you to communicate with the phone.
* [Kannel](http://www.kannel.org/) - Open Source WAP and SMS gateway.
* [Nexmo](https://www.nexmo.com/) - API for sending text messages.
* [PHP Classes](http://www.phpclasses.org/search.html?words=sms&go_search=1) - Several solutions to send SMS with PHP.
* [SMS Gateway](https://en.wikipedia.org/wiki/SMS_gateway)
* [SMS Gateway Android](https://smsgateway.me/) - Turn your Android phone into a SMS Gateway.
* [Twillio](https://www.twilio.com/) - API for sending text messages.
* Tutorials:
    * [Envato Tuts+](http://code.tutsplus.com/tutorials/how-to-send-text-messages-with-php--net-17693) - How to Send Text Messages with PHP.
    * [SitePoint](http://www.sitepoint.com/implement-two-way-sms-with-php/) - Implement Two-way SMS with PHP.
