

# GET minimal
curl https://api.github.com/users/paladinze

# GET including headers
curl -i https://api.github.com/users/defunkt

# POST Minimal
curl -d "args" protocol://address:port/url

# POST Custom
curl -X POST -H "Content-Type: application/json" -d '{"firstName":"First", "lastName":"Last"}' localhost:3000/users
