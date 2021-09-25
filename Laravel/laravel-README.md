برای نصب ماژول دیجی پی ابتدا دستور زیر را در مسیر root پروژه لاراول خود اجرا کنید

```
composer require mydigipay/laravel
```

بعد از نصب دستور زیر را اجرا کنید

```
php artisan vendor:publish
```

اکنون ماژول دیجی پی اماده استفاده است و میتوانید تنظیمات خود را به صورت env و یا در فایل config/digipay.php انجام دهید

برای انجام تراکنش به این صورت اقدام کنید‌: 

```php

public function pay(){

    $refID  = 12345;
    $mobile = "09121230000";

    $dp = Digipay::init();
    $dp->setAmount(10000);
    $dp->setCallback("https://test.com/callback");
    
    try{

        $dp->prepare($refID, $mobile);

        //save this
        $ticket = $dp->getTicket();

        return $dp->redirect();

    }catch(DigipayException $e){
        $error = $e->getMessage();
    }
}

```

و برای انجام verify در callback به این صورت اقدام کنید

```php

public function callback(Request $request){

    try{
        $result         = Digipay::verify($request);
        
        // transaction is successful

        $providerId     = $result['provider_id'];
        $trackingCode   = $result['tracking_code'];
        $amount         = $result['amount'];
        $result         = $result['result'];

    }catch(DigipayException $e){
        $error          = $e->getMessage();
    }

}

```
