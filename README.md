# Cookie-Notes
Cookies are stored in the request header in "cookies";

By default we cannot parse the information.  So in express and other programs you will need a middleware.

For express, use cookie-parser.  It makes the cookies header available under req.cookies.

Cool stuff

After installing it, use it in your server.
'''
import cookieParser from 'cookie-parser);
app.use(cookieParser())
'''
