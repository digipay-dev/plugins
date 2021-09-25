ابتدا پلاگین مورد نظر را به پروژه خود اضافه کنید

```
npm i --save digipay-gateway
```

و سپس برای انجام تراکنش به صورت زیر اقدام کنید 

```js
const dp = require('digipay-gateway')

let digipay = dp.initDigipay(username, password, clientID, clientSecret);

try{
    let url     = digipay.createTicket(amount, providerId, redirectUrl, cellNumber);

    // now redirect to the url

}catch(e){
 // handle error reporting
}

```

برای تایید تراکنش : 

```js
const dp = require('digipay-gateway')

let digipay = dp.initDigipay(username, password, clientID, clientSecret);

try{
    // get the tracking code from request (sent by POST method)
    digipay.verifyTicket(trackingCode)

    //transaction successful

}catch(e){
    // handle error reporting   
}

```
