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
```
def single_byte_xor(input, key):
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

# *CHALLENGE5*

We are given ```text:- Burning 'em, if you ain't quick and nimble I go crazy when I hear a cymbal``` 
and ```key:- ICE```. 

So we should xor with the text with key using the same key repeatedly.
```
def fixed_xor(bytes1, bytes2):
    assert len(bytes1) == len(bytes2)
    return bytes().join([bytes([a ^ b]) for a, b in zip(bytes1, bytes2)])

def repeating_key_xor(text, key):
    expanded_key = bytearray()
    for i in range(len(text)):
        expanded_key.append(key[i % len(key)])
    return fixed_xor(text, expanded_key)

print(repeating_key_xor(b"Burning 'em, if you ain't quick and nimble I go crazy when I hear a cymbal", b"ICE"))
```
We will get Bytes are using this program.
```b'\x0b67\'*+.cb,.ii*#i:*<c$ -b=c4<*&"c$\'\'e\'*(+/ i\ne.,e*1$3:e>+ \'c\x0ci+ (1e(c&0.\'(/'.encode('hex')```
By encoding the bytes into hex we get desired ouput
```
>>> b'\x0b67\'*+.cb,.ii*#i:*<c$ -b=c4<*&"c$\'\'e\'*(+/ i\ne.,e*1$3:e>+ \'c\x0ci+ (1e(c&0.\'(/'.encode('hex')
'0b3637272a2b2e63622c2e69692a23693a2a3c6324202d623d63343c2a26226324272765272a282b2f20690a652e2c652a3124333a653e2b2027630c692b20283165286326302e27282f'
```
