Cookie contains some information 

# Creating a cookie
- Javascript- Document.cookie
- Web server- Set-cookie header (response.setHeader("Set-cookie",["Setfromserver=1"])). Here the server sends cookies to the client and asks client to save it, Now on all future req the browser automatically attaches the saved data so the server knows who you are.

# Cookies properties
- Cookies are sent with every request
- Cookie scope
    * Domain = Domain is like a bucket where the cookie is stores, many cookies can be there in bucket
    * Path = You can set paths for the cookies (I want cookies to be sent on /login and not on /orders) document.cookie="Ishaancookie=1 ; path=/login"
- Expires, max age : If you dont specify the max age then the cookie will be destroyed the moment you close the browser
