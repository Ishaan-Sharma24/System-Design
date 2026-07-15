Cookie contains some information 

# Creating a cookie
- Javascript- Document.cookie
- Web server- Set-cookie header (response.setHeader("Set-cookie",["Setfromserver=1"])). Here the server sends cookies to the client and asks client to save it, Now on all future req the browser automatically attaches the saved data so the server knows who you are.

# Cookies properties
- Cookies are sent with every request
- Cookie scope
    * Domain = Domain is like a bucket where the cookie is stores, many cookies can be there in bucket
    * Path = You can set paths for the cookies (I want cookies to be sent on /login and not on /orders) document.cookie="Ishaancookie=1 ; path=/login"
- Expires, Max-age : If you dont specify the max age then the cookie will be destroyed the moment you close the browser(document.cookie="tempcookie=9; max-age=3min")
- Same site: Suppose we enter a website, and it has issued us cookie, now if we click on a link from that website will the cookie transfer? thats what same site tells ("document.cookie="securecookie1=2; samesite=strict" this means if you are going to a different site cookie will not go if on the same site cookie will go)

# Cookie types
- Session cookie: A cookie that doesn't have a max age or expiry 
- Permanent cookie: A cookie that has max age or expiry
- Httponly: Cookie that can only be sent from server and through HTTP, cannot be read by browser
- Secure Cookie: will only be sent to https domains
- Third party cookies: Suppose some ads are there in a website, so cookies are coming from the origin of the ads to the website
- Zombie cookies: Those cookies which recreate themselves even if you delete them, a zombie cookie intentionally hides duplicates of its tracking ID in multiple locations of your device. Even if your cookie storage looks empty, it silently grabs one of the hidden backups and resurrects the deleted cookie
