IB-PRE
======
An implementation of the Certificateless Public Key Cryptography in:<br/>
> S. S. Al-Riyami and K. G. Paterson, "Certificateless Public Key Cryptography," in Asiacrypt 2003<br/>

Available at: https://eprint.iacr.org/2003/126.pdf

In order to use this class install [Charm-Crypto library](https://github.com/JHUISI/charm/)

# Example
The following code is a full example of the provided library

```python
group = PairingGroup('SS512', secparam=1024)
clpkc = CLPKC_RP03(group)
(params, master_key) = clpkc.setup()
ID = 'user@email.com'
partial_private_key = clpkc.partial_private_key_extract(master_key, ID)
secret_value = group.random(ZR)
private_key = clpkc.set_private_key(partial_private_key, secret_value)
public_key = clpkc.set_public_key(params, secret_value)
msg = b"hello world!!!!!"
cipher_text = clpkc.encrypt(params, msg, ID, public_key)
plain_text = clpkc.decrypt(params, private_key, cipher_text)
print (plain_text)
```
