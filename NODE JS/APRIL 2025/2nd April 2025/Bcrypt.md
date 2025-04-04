
```js
const bcrypt = require("bcrypt");

const nSaltRounds = 16;
const sPlainText = "Meet is noob in minecraft";
const sOtherText = "Rishi is pro in minecraft";

let salt = bcrypt.genSaltSync(nSaltRounds);
const hash1 = bcrypt.hashSync(sPlainText, salt);

const hash2 = bcrypt.hashSync(sPlainText, nSaltRounds);

console.log(bcrypt.compareSync(sPlainText, hash1)); // true
console.log(bcrypt.compareSync(sPlainText, hash2)); // true
console.log(bcrypt.compareSync(sOtherText, hash2)); // false

```

```
$2b$10$nOUIs5kJ7naTuTFkBy1veuK0kSxUFXfuaOKdOKf9xYT0KKIGSJwFa
 |  |  |                     |
 |  |  |                     hash-value = K0kSxUFXfuaOKdOKf9xYT0KKIGSJwFa
 |  |  |
 |  |  salt = nOUIs5kJ7naTuTFkBy1veu
 |  |
 |  cost-factor => 10 = 2^10 rounds
 |
 hash-algorithm identifier => 2b = BCrypt
```

