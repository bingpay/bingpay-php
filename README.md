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
### Retrieve your wallet balance
The following implementation shows how eftch your bingpay wallet balance.

```php
// make sure to call the class Bingpay
$bingpay = new BingPay();

$bingpay->getBalance()->data->balance;

```

### Fetch all networks
The following implementation shows how fetch all networks.
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
The following implementation shows how perform airtime purchase.
```php
$bingpay->purchaseAirtime('$phone_number', $amount, $network_id)->message;
// returns a message
```
### Verify Phone Number
The following implementation shows how to verify if a phone number is correct, you can find list of all ISO codes [here](https://www.nationsonline.org/oneworld/country_code_list.htm).
```php
$bingpay->verifyNumber('$phone_number', $country_iso)->message;
// returns a message
```

### Fetch all banks
The following implementation shows how to fetch all Nigerian banks.
```php
$bingpay->fetchAllBanks();
// returns an array of all banks
```
### Resolve bank account details
The following implementation shows how to fetch bank account name from account details.
```php
$bingpay->resolveBank($bank_code, $account_number)->message;
// returns a message
```

### Fetch all data plans
The following implementation shows how to fetch all data plans for all networks.
```php
$bingpay->getAllDataPlan();
// returns an array of all data plans
```
### Fetch plans of a network
The following implementation shows how to fetch data plans from a network id.
```php
$bingpay->getDataPlan($network_id);
// returns an array of data plan
```
### Data Purchase
The following implementation shows how to perform data purchase.
```php
$bingpay->buyData('$phone_number', $plan_id, $network_id);
// returns a message
```
### Fetch network fee
The following implementation shows how to fetch fee in percentage before performing airtime to cash request.
```php
$bingpay->getNetworkFee($amount, $network_id)->message;
// returns a message
```
### Convert airtime to cash
The following implementation shows how to make an airtime to cash request.
```php
$bingpay->airtimeToCash($amount, $network_id, '$phone_number')->message;
// returns a message
```

### Fetch all bill services
The following implementation shows how fetch all bills available on Bingpay.
```php
$bingpay->getAllService();
// returns an array of all services
```
### Fetch service variation
The following implementation shows how to get service variation from a service id.
```php
$bingpay->getSingleService($service_id);
// returns an array of service
```
 ### Verify customer id
 The following implementation shows how to verify customer id such as smart card number, meter number etc.
 ```php
$bingpay->verifyCustomer($service_id,$customer_id,'prepaid')->message;
// returns a message
```
 ### Perform bill purchase
 The following implementation shows how to make a bill purchase.
  ```php
$bingpay->purchaseBill($service_id,$customer_id,$variation,$amount)->message;
// returns a message
```

### BVN Verification
The following implementation shows how to verify a Bank Verification Number.
```php
$bingpay->verifyBVN('$firstname', '$lastname', '$phone_number', '$bvn')->message;
// returns a message
```
