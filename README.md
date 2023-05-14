Keycloak (auth) + Krakend (API gateway) demo for Null Signal

Keycloak (https://keycloak.org) lets us handle authentication and authorization, including making and managing oauth clients.

Krakend is an API gateway that we can use to sit in front of the API, handle rate limiting and a bunch of auth for us.
Krakend can verify incoming auth tokens against keycloak and reject them before ever hitting the API server and the API
server can operate with a bit more trust.

https://designer.krakend.io/ can be used to edit the krakend config, which is repetitive and we should probably code-generate.

Kong is another good API Gateway option.

To run this:
```
# if you don't already have a null_signal docker network
docker network create null_signal
docker compose build
docker compose up -d
```

Then go to http://localhost:8080/, click the admin console, login with admin/password and set stuff up.

The API gateway is exposed at http://localhost:10000/.

This uses the shared null_signal network so it can talk to the NRDB API Server and the Token Display app can talk to this as well. 
