برای انجام تراکنش به صورت زیر اقدام کنید

```php
include "DPGateway.php";

$settings = [
    "type"          => "IPG",
    "username"      => "",
    "password"      => "", 
    "client_id"     => "",
    "client_secret" => "",
    "access_token"  => null,
    "refresh_token" => null
];

$updater = function($accessToken, $refreshToken){
    //save this data
};

$dp         = new DPGateway($settings,$updater);

try{

    $ticket     = $dp->createTicket($amount, $providerId, $redirectUrl, $cellNumber);
    $url        = $ticket['url'];
    $ticketID   = ticket['ticket'];

    //rediret to url
}catch(Exception $e){
    // handle error
}

```

برای کال بک به صورت زیر اقدام کنید : 

```php
try{

    $ticket     = $dp->verifyTicket($_POST['trackingCode']);
    //transaction successful

}catch(Exception $e){
    // handle error
}

