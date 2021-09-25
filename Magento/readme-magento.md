بعد از اکستراکت کردن فایل های فایل های داخل فولدر app را در مسیر اصلی نصب مجنتو کپی کنید
حالا
دستورات زیر را به ترتیب داخل ترمینال خود وارد کنید .


```
php bin/magento setup:upgrade
php bin/magento setup:di:compile
php bin/magento setup:static-content -f
php bin/magento cache:flush
```
پس از این ماژول به خوبی نصب شده و حالا در بخش تنظیمات اطلاعات مربوط به دیجی پی را وارد کنید
