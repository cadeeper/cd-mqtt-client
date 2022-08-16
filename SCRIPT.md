
## Script support
Script implemention is base on aviatorscript: https://github.com/killme2008/aviatorscript
### connection username/password script
The script will be executed before you connect to the server, you can use it to encode the username or encrypt the password.
Example: 
```
## example: base64.encode('str'), base64.decode('str');
let base64 = require('base64');
## example: hmac.md5Hex('data', 'key'), support functions: md5Hex, sha1Hex, sha224Hex, sha256Hex, sha384Hex, sha512Hex
let hmac = require('hmac');
## example: digest.md5Hex('str'), support functions: md5Hex, md2Hex, sha512Hex, sha384Hex, sha256Hex, sha1Hex
let digest = require('digest');
let base = require('base');

let username = base64.encode(#{username});
let password = hmac.md5Hex(#{password}, 'secret');
## this will return the replaced username and password
return base.simpleAuth(username, password);
```

### Support functions
#### base64
```
let base64 = require('base64');
let encoded = base64.encode('aaa');
let decoded = base64.decode('aaa');
```
#### digest
```
let digest = require('digest');
let hex = digest.md5Hex('aaa');
let hex = digest.md2Hex('aaa');
let hex = digest.sha512Hex('aaa');
let hex = digest.sha384Hex('aaa');
let hex = digest.sha256Hex('aaa');
let hex = digest.sha1Hex('aaa');
```

#### hmac
```
let hmac = require('hmac');
let hex = hmac.md5Hex('aaa', 'secret');
let hex = hmac.sha1Hex('aaa', 'secret');
let hex = hmac.sha224Hex('aaa', 'secret');
let hex = hmac.sha256Hex('aaa', 'secret');
let hex = hmac.sha384Hex('aaa', 'secret');
let hex = hmac.sha512Hex('aaa', 'secret');
```
#### other aviator functions
[aviator functions](https://www.yuque.com/boyan-avfmj/aviatorscript/ashevw?translate=en)

