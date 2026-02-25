# Cookie-Notes
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
