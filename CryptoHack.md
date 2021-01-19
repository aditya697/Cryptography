# ***CRYPTOHACKS***

## ***INTRODUCTION***

### *Finding Flag*

The flag is given in the question.

```FLAG:- crypto{y0ur_f1rst_fl4g)```

### *Great snakes*

By running the program we get the flag.

```FLAG:- crypto{z3n_0f_pyth0n}```

### *Networks Attacks*

We are given a .py file.
If we change buy:clothes to buy:flags and run the program we will get the answer.

```FLAG:- crypto{sh0pp1ng_f0r_fl4g5}```

## ***GENERAL***

### *ASCII*

We are given a list of ascii value if we convert them into text we get the flag.

```
ini_list = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
res = "" 
for val in ini_list:
      res = res + chr(val)
print ("Resultant string", str(res))
```

using this program we get the flag

```FLAG:- crypto{ASCII_pr1nt4bl3}```

### *HEX*

We are given a hex string. To get the flag we should decode from hex. We can use ```.decode('hex')```

Or by this progra we can obtain the flag.
```
x = '63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d'
byte_array = bytearray.fromhex(x)
print(byte_array)
```
We get the using the code.

```FLAG:- crypto{You_will_be_working_with_hex_strings_a_lot}```

## *Base64*

We are given a hex string. First we have to decode from hex.

Now the output of .decode('hex') or the above program we get string in bytes
```'r\xbc\xa9\xb6\x8f\xc1j\xc7\xbe\xeb\x8f\x84\x9d\xca\x1d\x8ax>\x8a\xcf\x96y\xbf\x92i\xf7\xbf'```

By encodeing the bytes using the following program we get the flag.

```
from base64 import b64encode
b64encode(byte_arr)
```

```FLAG:-crypto/Base+64+Encoding+is+Web+Safe/```

## *Bytes to Big Integers*

We are given long integers.

By using long_to_bytes , bytes_to_long we convert long integers to bytes and vice versa.

By using the following program we get the flag.
```
>>> from Crypto.Util.number import bytes_to_long, long_to_bytes    
>>> val = 11515195063862318899931685488813747395775516287289682636499965282714637259206269
>>> long_to_bytes(val) 
```

```FLAG:- crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}```

## *Encoding Challenge*

We are given a .py file. 

