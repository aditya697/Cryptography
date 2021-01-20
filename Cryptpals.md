# ***SET1*** 

### *CHALLENGE1*(Convert hex to base64)

We are a given,which should decoded from hex.
Then we have to do b64encoding to get the desired

```output:- SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t```

By using this we get the output
```
import base64
byte_array = bytearray.fromhex("49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d")
print(base64.b64encode(byte_array))
```

### *CHALLENGE2*(Fixed XOR)

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

### *CHALLENGE3*(Single-byte XOR cipher)

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

### *CHALLENGE5*(Implement repeating-key XOR)

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
### *CHALLENGE7*(AES in ECB mode)
 We are given a text file and we are the given ```key:-YELLOW SUBMARINE```
 
 In **AES Encryption/Decryption** the key size can be 16,32,48 . So here in our case the key lenght is 16.
 
 By decrypting using this code we can get the *AES ENCRYPTED MEESSAGE*. 
 ```
from Crypto.Cipher import AES
import base64
with open('7.txt') as fh:
    ciphertext = base64.b64decode(fh.read())
key = b'YELLOW SUBMARINE'
cipher = AES.new(key, AES.MODE_ECB)
plaintext = cipher.decrypt(ciphertext)
print(plaintext)
```
The decrypted text is 
```
b"I'm back and I'm ringin' the bell \nA rockin' on the mike while the fly girls yell \nIn ecstasy in the back of me \nWell that's my DJ Deshay cuttin' all them Z's \nHittin' hard and the girlies goin' crazy \nVanilla's on the mike, man I'm not lazy. \n\nI'm lettin' my drug kick in \nIt controls my mouth and I begin \nTo just let it flow, let my concepts go \nMy posse's to the side yellin', Go Vanilla Go! \n\nSmooth 'cause that's the way I will be \nAnd if you don't give a damn, then \nWhy you starin' at me \nSo get off 'cause I control the stage \nThere's no dissin' allowed \nI'm in my own phase \nThe girlies sa y they love me and that is ok \nAnd I can dance better than any kid n' play \n\nStage 2 -- Yea the one ya' wanna listen to \nIt's off my head so let the beat play through \nSo I can funk it up and make it sound good \n1-2-3 Yo -- Knock on some wood \nFor good luck, I like my rhymes atrocious \nSupercalafragilisticexpialidocious \nI'm an effect and that you can bet \nI can take a fly girl and make her wet. \n\nI'm like Samson -- Samson to Delilah \nThere's no denyin', You can try to hang \nBut you'll keep tryin' to get my style \nOver and over, practice makes perfect \nBut not if you're a loafer. \n\nYou'll get nowhere, no place, no time, no girls \nSoon -- Oh my God, homebody, you probably eat \nSpaghetti with a spoon! Come on and say it! \n\nVIP. Vanilla Ice yep, yep, I'm comin' hard like a rhino \nIntoxicating so you stagger like a wino \nSo punks stop trying and girl stop cryin' \nVanilla Ice is sellin' and you people are buyin' \n'Cause why the freaks are jockin' like Crazy Glue \nMovin' and groovin' trying to sing along \nAll through the ghetto groovin' this here song \nNow you're amazed by the VIP posse. \n\nSteppin' so hard like a German Nazi \nStartled by the bases hittin' ground \nThere's no trippin' on mine, I'm just gettin' down \nSparkamatic, I'm hangin' tight like a fanatic \nYou trapped me once and I thought that \nYou might have it \nSo step down and lend me your ear \n'89 in my time! You, '90 is my year. \n\nYou're weakenin' fast, YO! and I can tell it \nYour body's gettin' hot, so, so I can smell it \nSo don't be mad and don't be sad \n'Cause the lyrics belong to ICE, You can call me Dad \nYou're pitchin' a fit, so step back and endure \nLet the witch doctor, Ice, do the dance to cure \nSo come up close and don't be square \nYou wanna battle me -- Anytime, anywhere \n\nYou thought that I was weak, Boy, you're dead wrong \nSo come on, everybody and sing this song \n\nSay -- Play that funky music Say, go white boy, go white boy go \nplay that funky music Go white boy, go white boy, go \nLay down and boogie and play that funky music till you die. \n\nPlay that funky music Come on, Come on, let me hear \nPlay that funky music white boy you say it, say it \nPlay that funky music A little louder now \nPlay that funky music, white boy Come on, Come on, Come on \nPlay that funky music \n\x04\x04\x04\x04"
````
