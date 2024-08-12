---
layout: default
---
# Talking Web Module Walkthrough *(Levels 1-18)* - PwnCollege 
Practicality of the Module: Using curl or nc or python3 **(requests)** library we can forge our own http requests, and in order to solve the module challenges we need to issue an http request to `port 80` on localhost which throughout this module will be assigned to an IPv4 address of `127.0.0.1`, better interpreted as `http://127.0.0.1`, this is a layered module, meaning that the ideas presented in a level help you understand the next one more effectively.
## Level 1:
```
curl 127.0.0.1:80
```
## Level 2:
```
nc 127.0.0.1 80
GET / HTTP/1.1
```
## Level 3:
```
python3 import requests
r = requests.get('http://127.0.0.1:80')
print(r.text)
```
## Level 4:
Note: You're asked to modify your request that it correctly requests specific values from the server, within the **<>** provided is where you paste in level-specific values to be able to solve the challenge. This gets repeated along the way from this point on forward.
```
curl -H <"paste_host_header_value"> 127.0.0.1:80
```
## Level 5: 
```
nc 127.0.0.1 80
GET / HTTP/1.1
Host:<"paste_host_header_value">
```
## Level 6:
```
python3 import requests
headers = {'Host': '<"paste_host_header_value">'}
r = requests.get('http://127.0.0.1:80', headers=headers)
print(r.text)
```
## Level 7:
```
curl --request-target <"paste_in_path_value"> http://127.0.0.1
```
## Level 8:
```
nc 127.0.0.1 80
GET /<"paste_in_path_value"> HTTP/1.1
```
## Level 9:
```
python3 import requests
base_url = 'http://127.0.0.1'
path = '/<"paste_in_path_value">'
r = requests.get(base_url + path)
print(r.text)
```
Note: Now this is where the module builds up in complexity, providing you have knowledge on how to use python or any other tool in your disposal to aid in helping you forge the correct request, I chose python for its ease of use and how it's already incorporated in the module.
## Level 10:
```
python3
import urllib.parse
path=<"paste_in_path_value">
encoded_path = urllib.parse.quote(path)
print(encoded_path)

curl -G --request-target <"copy_encoded_path"> http://127.0.0.1
```
## Level 11:
```
python3 import urllib.parse
path=<"paste_in_path_value">
encoded_path = urllib.parse.quote(path)
print(encoded_path)

# Copy path, then use nc to forge the GET request

nc 127.0.0.1 80
GET /<"copy_encoded_path"> HTTP/1.1
```
## Level 12:
```
<python3 import urllib.parse, requests
path=<"paste_in_path_value">
encoded_path = urllib.parse.quote(path)
print(encoded_path)
base_url = 'http://127.0.0.1'
r = requests.get(base_url + encoded_path)
print(r.text)
```
## Level 13:
```
curl -G -d "a=<"paste_in_argument_value">" http://127.0.0.1
```
## Level 14:
```
nc 127.0.0.1 80
GET /?a=<"paste_in_argument_value"> HTTP/1.1
```
## Level 15:
```
<python3 import requests
params = {"a": <"paste_in_argument_value">}
base_url = "http://127.0.0.1"
r = requests.get(base_url, params)
print(r.text)
```
Note: For the next two levels, 2 arguments are provided, one value needs url encoding and one doesn't. Now some tools don't offer url encoding like netcat, but curl and python do.
## Level 16:
```
curl -G -d "a=<"paste_in_arg1_value">" --data-urlencode "b=<"paste_in_arg2_value">" http://127.0.0.1
```
## Level 17:
```
python3 import urllib.parse
non_encoded_arg2_value=(<"paste_in_given_value">)
encoded_arg2_value = urllib.parse.quote(non_encoded_arg2_value)

# Copy path, then use nc to forge the GET request

nc 127.0.0.1 80
GET /?a=<"paste_in_arg1_value">&b=<"encoded_arg2_value"> HTTP/1.1
```
## Level 18:
```
python3 import requests, urllib.parse
non_encoded_arg2_value=(<"paste_in_given_value">)
encoded_arg2_value = urllib.parse.quote(non_encoded_arg2_value)
params = {"a": <"paste_in_arg1_value">, "b": <"encoded_arg2_value">}
base_url = "http://127.0.0.1"
r = requests.get(base_url, params)
print(r.text)
```
[PwnCollege Modules List](./pwncol.md)
