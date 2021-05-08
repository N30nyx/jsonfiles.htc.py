# jsonfiles.htc.py
how to write to json files in python

# 1 - import json
```python
import json
```

# 2 - Create a function to start values, eg. login
```python
import json
def get_data():
  with open("data/template.json","r") as f:
  	users = json.load(f)

	return users
def signup(usr,pwd):
  users = get_data()
  users[usr] = {}
  users[usr]["password"] = pwd
  with open("data/template.json","w") as f:
		json.dump(users,f)
signup("eris","1234")
```
sign up basically sets the value to what it is given
in the part where we get_data()
we load the file as a function
meanwhile when we dump it, we are assigning the values and sending it into the json file
####
The difference is in loading we set it to read hence, the "r" and to dump it must be "w"
####
Ok so now we have our sign up which loads the account with the values given, in a json file it will be look like this
```json
{}
```
let's say the username was "eris" and the password was "1234"
```json
{"eris": {"password": "1234"}}
```
So to call that value we need to first load the json and then go for that value eg.
```python
import json
def get_pwd(username)
  users = get_data()
  password = users[username]["password"]
  print(password)
````
So with this if we called it as `get_pwd("eris")` it would print `1234`, so this is how we chec for the values we have against the values given
Moving on, let's say that the json file wasn't found so we add a checkjson function
```python
import json
import os
def check4json():
  try:
    os.system("cat data/template.json")
   except FileNotFoundError:
    os.system("touch data/template.json")
    os.system("echo {} > data/template.json")
```
Ok everything is set up for utilising the json values so now let's add the input part
```python
import json
import os
def get_data():
  with open("data/template.json","r") as f:
  	users = json.load(f)

	return users
def signup(usr,pwd):
  users = get_data()
  users[usr] = {}
  users[usr]["password"] = pwd
  with open("data/template.json","w") as f:
		json.dump(users,f)
def check4json():
  try:
    os.system("cat data/template.json")
   except FileNotFoundError:
    os.system("touch data/template.json")
    os.system("echo {} > data/template.json")
query = input("username: ")
print("query")
query2 = input("password: ")
print(query2)
users = get_data()
if users[query] not in users:
  print("signing you up, retry the login now")
  signup(query,query2)
if users[query] in users:
  if query2 == users[query]["password"]:
    print("logged in....")
  if query2 != users[query]["password"]:
    print("password wrong retry later")
```
so what we've done is taken the values given, and checked it with the values we have
since we have "eris" in username, if anyone types anything but eris they will be registered
let's say they type eris, we then check wether the password matches the password set.
That is how to write, load and use json files in python.
