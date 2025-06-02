## The website comes up, but when you click on an APD, you get the dashboard, but the APD list says loading until the screen goes white screen
**The DevTools Error looks like this:**

![Screen Shot 2022-04-28 at 6 18 52 PM](https://user-images.githubusercontent.com/62778/165857086-49d497f4-6384-47ab-9351-93b06a6c9f6a.png)


**The AWS errors in mongod.log looks like this:**
```
{
    "t": {
        "$date": "2022-04-28T17:22:47.504-04:00"
    },
    "s": "I",
    "c": "ACCESS",
    "id": 20249,
    "ctx": "conn1",
    "msg": "Authentication failed",
    "attr": {
        "mechanism": "SCRAM-SHA-256",
        "speculative": true,
        "principalName": "eapd_admin_preview",
        "authenticationDatabase": "admin",
        "remote": "127.0.0.1:34454",
        "extraInfo": {},
        "error": "UserNotFound: Could not find user \"eapd_admin_preview\" for db \"admin\""
    }
}
```