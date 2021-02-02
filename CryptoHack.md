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

### *Base64*

We are given a hex string. First we have to decode from hex.

Now the output of .decode('hex') or the above program we get string in bytes
```'r\xbc\xa9\xb6\x8f\xc1j\xc7\xbe\xeb\x8f\x84\x9d\xca\x1d\x8ax>\x8a\xcf\x96y\xbf\x92i\xf7\xbf'```

By encodeing the bytes using the following program we get the flag.

```
from base64 import b64encode
b64encode(byte_arr)
```

```FLAG:-crypto/Base+64+Encoding+is+Web+Safe/```

### *Bytes to Big Integers*

We are given long integers.

By using long_to_bytes , bytes_to_long we convert long integers to bytes and vice versa.

By using the following program we get the flag.
```
>>> from Crypto.Util.number import bytes_to_long, long_to_bytes    
>>> val = 11515195063862318899931685488813747395775516287289682636499965282714637259206269
>>> long_to_bytes(val) 
```

```FLAG:- crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}```

### *Encoding Challenge*

We are given a .py file. If we rreach 100th level we will get the flag.

## ***XOR***

### *XOR Starter*

We are given a word. And that word is XORed with 13.
So we conver word in binary then XOR with binary of 13. We get the flag
```
data = "label"
flag = ''
for c in data:
    flag += chr(ord(c) ^ 13)
print(flag)
```
Since the flag mentioned is crypto{string}.

```FLAG:- crypto{aloha}```

## *XOR Properties*

We are given
```
>>>KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
>>>KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
>>>KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
>>>FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
```
We have to first decode from hex.By using the program we can get the flag coverting into hex.
```
import codecs
k1 = int('a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313', 16)
k2_3 = int('c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1', 16)
flag = int('04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf',16)
flag = k1 ^ k2_3 ^ flag
print(codecs.decode(('%x' %flag),'hex_codec'))
```
```FLAG:- crypto{x0r_i5_ass0c1at1v3}```

### *Favorite Bytes*

We are given a hex,which we have decode.
Then since it is single byte xor the length of the key is 1.
Therefore we can say there will be 256 that we try and xor to get the flag.
By using the the code we can find the flag.
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

decoded = bytearray.fromhex("73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d")
result = {}
for i in range(256):
    result[i] = (single_byte_xor(decoded, i))
for s in result.values():
    if ("crypto" in s):
        print(s)
```
 
```FLAG:-crypto{0x10_15_my_f4v0ur173_by7e}```

### *You either know, XOR you don't*

We are given a hex,which we have to decode.
Here the key length is unkown,So we have to brute to get the flag.
But we know we know the starting few words of the Flag. 
By using we can find that we can find the flag. By using this program
```
def brute(input, key):
    if len(input) != len(key):
        return "Failed!"

    output = b''
    for b1, b2 in zip(input, key):
        output += bytes([b1 ^ b2])
    try:
        return output.decode("utf-8")
    except:
        return "Cannot Decode some bytes"

cipher = bytearray.fromhex("0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104")
key_part = brute(cipher[:7], "crypto{".encode())
key = (key_part + "y").encode()
key += key * int((len(cipher) - len(key))/len(key))
key += key[:((len(cipher) - len(key))%len(key))]
plain = brute(cipher, key)
print(plain)
```

```FLAG:-crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}```

# ***RSA***

## ***STARTER***

### *RSA STARTER 1*
 
 We are asked to find ``101^17 mod 22663``
 
 By using ``pow(101,17,22663)``.
 
 ```FLAG:-crypto{19906}```
 
 ### *RSA STARTER 2*
 
 We are given number,exponent,p,q. By doing pxq we get n. Then by using ```pow(12,65537,391)```.
 
```FLAG:-crypto{301}```

### *RSA STARTER 3*

We given p and q. We have to find euler's totient. ```e = (p-1) x (q-1)```

```FLAG:-crypto{882564595536224140639625987657529300394956519977044270821168}```

### *RSA STARTER 4*

We are given p,q and e. We have to do find "d".

By using the code we get the flag.
```
from Crypto.Util.number import inverse
p = 857504083339712752489993810777
q = 1029224947942998075080348647219
e = (p-1) * (q-1)
d = inverse(65537, e)
print(d)
```
```FLAG:-crypto{121832886702415731577073962957377780195510499965398469843281}```

### *RSA STARTER 5*

We are given n,e and c. We have to decrypt cipher using d.

By using the code we can get the flag.
```
from Crypto.Util.number import inverse
c = 77578995801157823671636298847186723593814843845525223303932
n = 882564595536224140639625987659416029426239230804614613279163
p = 857504083339712752489993810777
q = 1029224947942998075080348647219
e = (p-1) * (q-1)
d = inverse(65537, e)
print(pow(c,d,n))
```
```FLAG:-crypto{13371337}```

## ***PRIMES PART 1***

### *FACTORING*

We are given a number. We are asked divide into 2 primes.
We can use factordb to get the primes.

```FLAG:-crypto{19704762736204164635843,25889363174021185185929}```

### *INFERIOUS PRIME*

We are given output.txt and and .py files. In the output file we are given c,e,n.

By getting primes of n and by using this code we get the flag.
```
import gmpy2
import codecs

if __name__ == '__main__':
    c = 39207274348578481322317340648475596807303160111338236677373
    n = 742449129124467073921545687640895127535705902454369756401331
    e = 3

    p = 752708788837165590355094155871
    q = 986369682585281993933185289261

    l = gmpy2.lcm(p-1, q-1)
    gcd, u, v = gmpy2.gcdext(e, l)

    while u < 0:
        u += l
    m = pow(c, u, n)
    print(m)
    print(codecs.decode(('%x'%m),'hex_codec'))
```
```FLAG:-crypto{N33d_b1g_pR1m35}```

### *MONOPRIME*

We are given a output.txt. From question heading we can understand that it is monoprime it doesn't have 2 primes.

By using the code we can get the flag.
```
from Crypto.Util.number import inverse,long_to_bytes

n = 171731371218065444125482536302245915415603318380280392385291836472299752747934607246477508507827284075763910264995326010251268493630501989810855418416643352631102434317900028697993224868629935657273062472544675693365930943308086634291936846505861203914449338007760990051788980485462592823446469606824421932591
e = 65537
ct = 161367550346730604451454756189028938964941280347662098798775466019463375610700074840105776873791605070092554650190486030367121011578171525759600774739890458414593857709994072516290998135846956596662071379067305011746842247628316996977338024343628757374524136260758515864509435302781735938531030576289086798942 

phi = n-1
d = inverse(e,phi)
print(long_to_bytes(pow(ct, d, n)))
```
```FLAG:-crypto{0n3_pr1m3_41n7_pr1m3_l0l}```

### *MANYPRIMES*

We get are given output.txt . From question heading we can understand that it has more than 2 primes.

By using the code we get the flag.
```
from gmpy2 import *
import codecs

n = 580642391898843192929563856870897799650883152718761762932292482252152591279871421569162037190419036435041797739880389529593674485555792234900969402019055601781662044515999210032698275981631376651117318677368742867687180140048715627160641771118040372573575479330830092989800730105573700557717146251860588802509310534792310748898504394966263819959963273509119791037525504422606634640173277598774814099540555569257179715908642917355365791447508751401889724095964924513196281345665480688029639999472649549163147599540142367575413885729653166517595719991872223011969856259344396899748662101941230745601719730556631637

c = 320721490534624434149993723527322977960556510750628354856260732098109692581338409999983376131354918370047625150454728718467998870322344980985635149656977787964380651868131740312053755501594999166365821315043312308622388016666802478485476059625888033017198083472976011719998333985531756978678758897472845358167730221506573817798467100023754709109274265835201757369829744113233607359526441007577850111228850004361838028842815813724076511058179239339760639518034583306154826603816927757236549096339501503316601078891287408682099750164720032975016814187899399273719181407940397071512493967454225665490162619270814464

e = 65537

primes = [9282105380008121879,9303850685953812323,9389357739583927789,10336650220878499841,10638241655447339831,11282698189561966721,11328768673634243077,11403460639036243901,11473665579512371723,11492065299277279799,11530534813954192171,11665347949879312361,12132158321859677597,12834461276877415051,12955403765595949597,12973972336777979701,13099895578757581201,13572286589428162097,14100640260554622013,14178869592193599187,14278240802299816541,14523070016044624039,14963354250199553339,15364597561881860737,15669758663523555763,15824122791679574573,15998365463074268941,16656402470578844539,16898740504023346457,17138336856793050757,17174065872156629921,17281246625998849649]

totient = 1

for i in primes:
	totient *= (i - 1)

assert gcd(e, totient) == 1

d = invert(e, totient)

get_context().precision=1000

m = powmod(c, d, n)
print(m[2:-1])
print(codecs.decode(('%x'%m),'hex_codec'))
```
```FLAG:-crypto{700_m4ny_5m4ll_f4c70r5}```


