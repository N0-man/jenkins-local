# Jenkins Local
Test your JENKINSFILE locally
### Build
```
docker-compose up -d
```
Once started Jenkins should be available on http://localhost:8080/. First time login requries adminstrative password which can be fetched from logs. You can then choose to install recomended plugins and proceed.
### Logs
```
docker logs jenkins | less
```
watch out for below key
```
*************************************************************
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

f288816a3c954fb7b66f6f8120fe86b3

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
```

### Connect Github remote to local Jenkins
1) `brew install ngrok` and [configure on your local](https://dashboard.ngrok.com/get-started/setup)
2) Expose local jenkins on internet through ngrok tunnel `ngrok http --host-header=localhost 8080`
3) Setup webhook on your github repo (settings/webhooks). Add the ngrok https url under payload url e.g. `https://dec2-128-106-1-171.ngrok-free.app/github-webhook/`. You can dissable SSL verification
4) Remember to update the ngrok webhook url everytime you restart the ngrok tunnel
