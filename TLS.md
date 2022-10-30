## Encrypt - Decrypt

[rsa](https://en.wikipedia.org/wiki/RSA_(cryptosystem))  
[spki](https://en.wikipedia.org/wiki/Simple_public-key_infrastructure)   
[X.509](https://en.wikipedia.org/wiki/X.509)  
[pem](https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail)  
[pkcs8](https://en.wikipedia.org/wiki/PKCS_8)  
[aes](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)  


```js
const crypto = require('crypto');

const keyPair = crypto.generateKeyPairSync('rsa', {
    modulusLength: 520,
    publicKeyEncoding: {
        type: 'spki',
        format: 'pem'
    },
    privateKeyEncoding: {
    type: 'pkcs8',
    format: 'pem',
    cipher: 'aes-256-cbc',
    passphrase: 'secret'
    }
});



//keyPair

const plaintext = "hemligt hemligt";
const encrypted = crypto.privateEncrypt({key: keyPair.privateKey, passphrase: 'secret'}, Buffer.from(plaintext));

encrypted

const decrypted = crypto.publicDecrypt( keyPair.publicKey, Buffer.from(encrypted) );

decrypted.toString();
```
