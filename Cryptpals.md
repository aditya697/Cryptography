# ***SET1*** 

## *CHALLENGE1*

We are a given,which should decoded from hex.
Then we have to do b64encoding to get the desired

```output:- SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t```

By using this we get the output
```
import base64
byte_array = bytearray.fromhex("49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d")
print(base64.b64encode(byte_array))
```

## *CHALLENGE2*

We are given to strings in hex.

```1c0111001f010100061a024b53535009181c```

```686974207468652062756c6c277320657965```

So we have to decode from hex and xor them to 
the desired ```output:- 746865206b696420646f6e277420706c6179```

By using the program we will get a string 
```
import codecs
dec1 = int("1c0111001f010100061a024b53535009181c", 16)
dec2 = int("686974207468652062756c6c277320657965", 16)
xor = dec1 ^ dec2
print(codecs.decode(('%x' %xor),'hex_codec'))
```

We get a ```string:-b"the kid don't play"```

By encoding this string as hex we get the ouput.
```
>>> b"the kid don't play".encode('hex')
'746865206b696420646f6e277420706c6179'
```

## *CHALLENGE3*

We are given a hex,which we have to decode to get the mssg.

By using the program we outputs from that we will have meaningfull message that is readable.
```def single_byte_xor(input, key):
    if len(chr(key)) != 1:
      raise "KEY LENGTH EXCEPTION: In single_byte_xor key must be 1 byte long!"

    output = b''
    for b in input:
        output += bytes([b ^ key])

    try:
        return output.decode("utf-8")
    except:
        return "Cannot Decode some bytes"

decoded = bytearray.fromhex("1b37373331363f78151b7f2b783431333d78397828372d363c78373e783a393b3736")
result = {}
for i in range(256):
    result[i] = (single_byte_xor(decoded, i))
for s in result.values():
        print(s)
```

The message is ```Cooking MC's like a pound of bacon```.


