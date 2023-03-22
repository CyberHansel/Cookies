# Cookies

The Secure flag specifies that the cookie may only be transmitted using HTTPS connections (SSL/TLS encryption)  
Cookie attributes can include `domain, expires, max-age, secure, and httponly` atributes that tells browser how to treat them.  

* secure - browsers will only send that cookie when visiting HTTPS sites.
* HttpOnly - browsers won’t allow any scripting languages, such as JavaScript, to read that cookie’s valueimportant when talk about Cross site scripting!
* expires - indicate date when a cookie should expire and the browser should destroy it. 
* max-age is the number of seconds until the cookie expires and is formatted as an integer (max-age=300).   

In addition to attributes, cookies can contain a name/value pair, which consists of an identifier and an associated value that is passed to a website  
(the cookie’s domain attribute defines the site to pass this information to). sites are free to choose their own name/value pairs.  

The first flag we need to set up is HttpOnly flag. By default, when there’s no restriction in place, cookies can be transferred not only by HTTP, but any JavaScript files loaded on a page can also access the cookies. This ability can be dangerous because it makes the page vulnerable to cross-site scripting (XSS) attack. The only way to restrict this is by setting HttpOnly flag, which means the only way cookies are sent is via HTTP connection, not directly through other means (i.e., JavaScript).

Edit the web.config file of your web app 
<system.web>  
  ...  
  <httpCookies httpOnlyCookies="true" requireSSL="true" />  
  ...  
</system.web>  

Secure flag on the JSESSIONID cookie.
But the JSESSIONID is still not yet SECURE.

XXS sending link with pages on site that you are already authenticated
