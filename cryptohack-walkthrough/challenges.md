---
layout: default
---
# Introductory Challenges to Cryptography - CryptoHack
Disclaimer: I'm only allowed to post challenge solutions for challenges that consist of 25 points or less, and are introductory challenges according to cryptohack's instructions.

## Challenge: ASCII
```python
#!/usr/bin/python3
# Task: Provided is an ASCII encoded integer array, convert them to characters to get the flag.

text = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
print("the flag is:")
print("".join(chr(i) for i in text))
```
## Challenge: Base64
```python
#!/usr/bin/python3
#Task: a hex string, decode to bytes and then encode in b64

hex = "72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf"
hex2bytes = bytes.fromhex(hex)
import base64 as b64
b64_encoding = b64.b64encode(hex2bytes)
print(b64_encoding)
```

[Back To Main Page](../..)
