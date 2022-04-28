# Installation

Using composer
```
composer install bingpay/bingpay-php
```
Add to your PHP code by including the index.php file
```require_once "__DIR__/bingpay-php/index.php";```

# Usage
## Configuration
Download the repo, head over to index.php and edit the addPrivateKey() by adding your key. (Remember to always keep your private key Private!!!)
  ```php 
   // call the connection class
        $connection = new Connection();

        // Add your private key here
        $connection->addPrivateKey('1dd501141dffd9d68f254b241f05871b8f10754c90f4832ad9');
        
  ```
### To retrieve your wallet balance

```php
// make sure to call the class Bingpay
$bingpay = new BingPay();

$bingpay->getBalance()->data->balance;

```

### To fetch all networks

```php
 var_dump($bingpay->fetchAllNetwork());
// returns an array of all networks

// you can loop through the arrays from the data property
foreach($bingpay->fetchAllNetwork()->data as $data){
    echo 'Network Provider: '.$data->name;
    echo '<br>';
    echo 'Network Note: '.$data->note;
    echo '<br>';
}
```
### Airtime Purchase
```php
$bingpay->purchaseAirtime('$phone_number', $amount, $network_id)->message;
// returns a message
```
### Verify Phone Number
```php
$bingpay->verifyNumber('$phone_number', $country_iso)->message;
// returns a message
```

### Fetch all banks
```php
$bingpay->fetchAllBanks();
// returns an array of all banks
```
### Resolve bank account details
```php
$bingpay->resolveBank($bank_code, $account_number)->message;
// returns a message
```

### Fetch all data plans
```php
$bingpay->getAllDataPlan();
// returns an array of all data plans
```
### Fetch plans of a network
```php
$bingpay->getDataPlan($network_id);
// returns an array of data plan
```
### Data Purchase
```php
$bingpay->buyData('$phone_number', $plan_id, $network_id);
// returns a message
```
### Fetch network fee
```php
$bingpay->getNetworkFee($amount, $network_id)->message;
// returns a message
```
### Convert airtime to cash
```php
$bingpay->airtimeToCash($amount, $network_id, '$phone_number')->message;
// returns a message
```

### Fetch all bill services
```php
$bingpay->getAllService();
// returns an array of all services
```
### Fetch service variation
```php
$bingpay->getSingleService($service_id);
// returns an array of service
```
 ### Verify customer id
 ```php
$bingpay->verifyCustomer($service_id,$customer_id,'prepaid')->message;
// returns a message
```
 ### Perform bill purchase
  ```php
$bingpay->purchaseBill($service_id,$customer_id,$variation,$amount)->message;
// returns a message
```

### Verify BVN Number
```php
$bingpay->verifyBVN('$firstname', '$lastname', '$phone_number', '$bvn')->message;
// returns a message
```
