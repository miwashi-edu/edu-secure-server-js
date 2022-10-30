# Hashing

```js
const crypto = require('crypto');
var bf = require('bruteforce');

const password = "abaa";
const secretHash = crypto.createHash('md5').update(password).digest('hex');//sha512

const hack = (password) => {
  const hash = crypto.createHash('md5').update(password).digest('hex');
    console.log(secretHash === hash);
}

bf({
  len: password.length,
  chars: ['a', 'b'],
  step: hack
});

```
