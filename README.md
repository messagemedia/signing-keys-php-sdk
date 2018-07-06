# MessageMedia Signature Key Management PHP SDK
[![Travis Build Status](https://api.travis-ci.org/messagemedia/signing-keys-php-sdk.svg?branch=master)](https://travis-ci.org/messagemedia/signing-keys-php-sdk)
[![PHP version](https://badge.fury.io/ph/messagemedia%2Fsigningkeys-sdk.svg)](https://badge.fury.io/ph/messagemedia%2Fsigningkeys-sdk)

The MessageMedia Signature Key API provides a number of endpoints for managing key used to sign each unique request to ensure security and the requests can't (easily) be spoofed. This is similar to using HMAC in your outbound messaging (rather than HTTP Basic).

![Isometric](http://i64.tinypic.com/2lo3n8p.jpg)

## ⭐️ Installing via Composer
Run the Composer command to install the latest stable version of the Messages SDK:
```
composer require messagemedia/signingkeys-sdk
```

## 🎬 Get Started
It's easy to get started. Simply enter the API Key and secret you obtained from the [MessageMedia Developers Portal](https://developers.messagemedia.com) into the code snippet below.

### 🚀 Create a signature key
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$bodyValue = "{   
  \"digest\": \"SHA224\",   
  \"cipher\": \"RSA\"
}";
$body = APIHelper::deserialize($bodyValue);

$result = $signatureKeyManagement->createSignatureKey($body);

```

### 📥 Get signature key details
You can get a key_id by looking at the id of the signature key created from the response of the above example.
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$keyId = 'key_id';

$result = $signatureKeyManagement->getSignatureKeyDetail($keyId);

```

### 📥 Get signature keys list
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$result = $signatureKeyManagement->getSignatureKeyList();

```

### ❌ Delete signature key
You can get the key_id by looking at the ids of the signature keys returned from the response of the `Get signature keys list` example.
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$keyId = 'key_id';

$signatureKeyManagement->deleteSignatureKey($keyId);

```

### ☑️ Enable a signature key
You can get the key_id by looking at the ids of the signature keys returned from the response of the `Get signature keys list` example.
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$body = new EnableSignatureKeyRequest({
  "key_id": "7ca628a8-08b0-4e42-aeb8-960b37049c31"
});

$result = $signatureKeyManagement->updateEnableSignatureKey($body);

```

### 📥 Get enabled signature key
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$result = $signatureKeyManagement->getEnabledSignatureKey();

```

### 🚫 Disable an enabled signature key
```php
require_once "../vendor/autoload.php";

$basicAuthUserName = 'basicAuthUserName'; // The username to use with basic authentication
$basicAuthPassword = 'basicAuthPassword'; // The password to use with basic authentication

$client = new MessageMediaSigningKeysLib\MessageMediaSigningKeysClient($basicAuthUserName, $basicAuthPassword);
$signatureKeyManagement = $client->getSignatureKeyManagement();

$signatureKeyManagement->deleteDisableTheCurrentEnabledSignatureKey();

```

## 📕 Documentation
Check out the [full API documentation](DOCUMENTATION.md) for more detailed information.

## 😕 Need help?
Please contact developer support at developers@messagemedia.com or check out the developer portal at [developers.messagemedia.com](https://developers.messagemedia.com/)

## 📃 License
Apache License. See the [LICENSE](LICENSE) file.
