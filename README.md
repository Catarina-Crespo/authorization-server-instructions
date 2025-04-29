# Authorization Server Instructions

This README file specifies the instructions for using the oauth server.

# Step 1: Register the Client Application

To register the client application you want to use, send a cURL request to the server with:
```
curl -X POST https://oauth-server-zosn.onrender.com/api/register/client \
     -H "Content-Type: application/json" \
     -d '{"clientID": "<some_client_id>", "clientSecret": "<some_client_secret>", "redirect_uris" : "<some_uri>"}'
```

If the client is registered successfully, you'll receive a response with:
```
{
    client_id: clientID,
    client_secret: clientSecret,
}
```

# Step 2: Register the User

To register the user you want to login with, send a cURL request to the server with:

```
curl -X POST http://localhost:3000/api/register/user \
     -H "Content-Type: application/json" \
     -d '{"username": "<some_username>", "password": "<some_password>"}'
```

If the user is registered successfully, you'll receive a response with:

```
{
    id: user_id,
    username,
}
```

# Step 3: Configure the Client Application

Afterwards, you'll need to configure your client by providing the OAuth server URL. For that, make sure you have the following lines (if using Express):

```
authorizationURL: "https://oauth-server-zosn.onrender.com/authorize",
tokenURL: "https://oauth-server-zosn.onrender.com/token",
callbackURL: "<your-client-url>/auth/provider/callback",
```

# Step 4: Start the Authorization Flow


