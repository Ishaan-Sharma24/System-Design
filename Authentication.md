# JWT 
Method to securely transmit info between parties as JSON objects.
- It has headers, payload and signature (encoded by base64)
    * Header has the token type like JWT and algorithm being used RSA, SHA256 etc
    * Payload is where you store the claims.
    * SIgning is like sealing an envelope wiht a wax stamp to ensure it hasn't been tampered with 
            ** Symmetric signing algo like SHA 256 uses shared secret key for both signing and verification
            ** Asymmetric algo like RSA use public private key pair, private key is used to sign it and public key to open and read it. Remember the payload is not encrypted, and anyone can see the payload because it is public but data cannot be altered( re-signed ) without a private key. if someone changes the data he has to resign it so the server will get to know somehting is changed because public key will not match 
    ## Flaws
    - If the token is stolen, we can't do anything about it. Since the system is statless, there is no entry stored in db that you can ask to delete if token is stolen. Hacker can use the token and can get confidential data; so the token must be short lived
    - But can't force users to login every 15 mins right so we need a way to get new JWT every 15 min Thats why refresh tokens were invented.
    - Refresh token is a JWT token that you store in a db
    ## Refresh Token
    This concept makes the system Statefull, now when the user login two tokens are provided by the server one is jwt token other is refresh token with a life of one day or more and entry of refresh token is stored in db, refresh token should be tightly secured because if that is stolen then no one can save you. so once the jwt is expired (say in 15 min) the server check the refresh token attached with the req and queries the db to check if that is authentic and provides a new JWT to the user.

# Session based 
 In this type of authentication, when a user signs up with username and password the server creates a session entry in the db with the session id and metadata containing information about the user, And a session token is sent back to the client. Now with every future request, the token is attached through cookies, header, body and for each request the server queries the db to check if the session token is there before sending response back.
 ## Flaw
  - For every request made, the application queries the db this brings latency into the system.
  - This system is statefull becasue the server is keeping some information about the user, it breaks the Restful nature.