
## Script support
Script implemention is base on aviatorscript: https://github.com/killme2008/aviatorscript
### connection username/password script
The script will be executed before you connect to the server, you can use it to encode the username or encrypt the password.
#### Example: 
encode and encrypt
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

get from remote server
```
let http = require('http');
let body = '{"mac": "FAKE-MAC-ADDRESS"}'
let headers = seq.map('Content-Type', 'application/json');
let result = http.post('http://localhost:8080', body, headers);
let code = result['statusCode'];
let body = result['mapBody'];
return base.simpleAuth(body.username, body.password);
```



### base usage
#### Array, Collections and Map
create a typed array by *seq.array(type, ..args)*
```
let array = seq.array(int, 1, 2, 3, 4);
let a1 = array[0];
```

create map by *seq.map(k1, v1, k2, v2 ...)*
```
let m = seq.map("k1", 1, "k2", 2, "3k", 3);

## get keys
let k1 = m.k1;
let k2 = m["k2"];
let k3 = seq.get(m, "3k");

## set keys
m.s1 = 1;
m["s2"] = 2;
seq.put(m, s3, 3);
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

#### http
http lib support get and post method.
```
let http = require('http');
let jsonBody = '{"param": "value", "praram1", "value1"}';
let headers = seq.map('Content-Type', 'application/json');
## response struct:
## mapBody is a map if the response body can be converted to json
## {statusCode: int, body: string, mapBody: map}
let response = http.post('http://xxx.com', jsonBody, headers);
let body = response.mapBody;
let username = body.username;
let password = body.passwor;

let response = http.get('url', headers);
...
```



#### other aviator functions
[aviator functions](https://www.yuque.com/boyan-avfmj/aviatorscript/ashevw?translate=en)

