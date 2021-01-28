# ***BASE BASE BASE***

We are given a cipher text.
```ciphertext:R1k0U0FOVEZFQTNER0lCWEdRUURNTlJBR1pRU0FOM0NFQTNERUlCVEdRUURPTVpBR01aU0FOWlRFQTJXTUlCVEdRUURPTVJBR01aU0FOTEdFQTNER0lCVEdBUURHTUJBR01ZQ0FNWlFFQVpUQUlCVEdBUURHTUJBR01ZQ0FOVERFQTNXST09PQ==```

First we have to do BASE64 decoding, we get base 32
```GY4SANTFEA3DGIBXGQQDMNRAGZQSAN3CEA3DEIBTGQQDOMZAGMZSANZTEA2WMIBTGQQDOMRAGMZSANLGEA3DGIBTGAQDGMBAGMYCAMZQEAZTAIBTGAQDGMBAGMYCANTDEA3WI===```

Then we have to do BASE32 decoding, we get hex```69 6e 63 74 66 6a 7b 62 34 73 33 73 5f 34 72 33 5f 63 30 30 30 30 30 30 30 30 6c 7d```

By decoding from hex we get the flag.

```FLAG:-inctfj{b4s3s_4r3_c00000000l}```

# ***VINEGAR_V1***

We are given a cipher text. ```ciphertext:-ioeqdi{siwcdke_tjrdelf_uesefmg}```
Since the question says poured with ``abcxyz`` i.e the key.

By using the program we can get the flag
```
def decrypt(ciphertext, key):
    key_length = len(key)
    key_as_int = [ord(i) for i in key]
    ciphertext_int = [ord(i) for i in ciphertext]
    plaintext = ''
    for i in range(len(ciphertext_int)):
        value = (ciphertext_int[i] - key_as_int[i % key_length]) % 26
        plaintext += chr(value + 0x61)
    return plaintext

print(decrypt("ioeqdisiwcdketjrdelfuesefmg", "abcxyz"))
```

```FLAG:-inctfj{shuffle_shuffle_shuffle}```
