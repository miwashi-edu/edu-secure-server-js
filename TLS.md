## Encrypt - Decrypt

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
