# Cookie-Notes
Install:
```
npm i cookie-parser
```
Cookies are stored in the request header in "cookies";

By default we cannot parse the information.  So in express and other programs you will need a middleware.

For express, use cookie-parser.  It makes the cookies header available under req.cookies.

Cool stuff

After installing it, use it in your server.
```
import cookieParser from 'cookie-parser';
```
```
app.use(cookieParser())
```

To use it, you can try to access a cookie by name, here is an example below:
```
app.get('/getcookie', (req, res) => {
    // Access a specific cookie by name
    const myCookieValue = req.cookies.myCookie;
    console.log('Cookies: ', req.cookies);
    res.send(`Value of myCookie: ${myCookieValue}`);
});
```

To set the cookie value set the value as a response.  Like this.
```
// res.cookies('cookieName', 'value', {options})
```

Here is an example:
```
app.get('/set-cookie', (req, res) => {
    res.cookie('myCookie', 'cookie_value', { maxAge: 3600000 }); // Cookie expires in 1 hour
    res.send('Cookie set successfully');
});
```

Important security options:
- Set httpOnly flag (helps with xss)
- You can also use signed cookies as it is a feature with cookie-parser.  Signed cookies can be accesed with req.signedCookies
- Options is an object 
- secret is optional but will not parse signed cookies if no secret is passed

Reminder, you set the options when you res.cookie(), it is the third parameter.  First is name, second is value.

Common options:
- httpOnly(Prevents JS from reading the cookie) 
- secure(Only send over https) (will not work in localhost unless its using https.  So good practice to set a dev environmental variable to base it off on)
- maxAge(milliseconds)
- sameSite(CSRF protection) - must be a string, and the options are 'strict', 'lax', 'none'
