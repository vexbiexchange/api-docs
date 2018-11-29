# Introduction

Welcome to the Vexbi API! We at Vexbi provide a simple and robust RESTful API enabling any service or company operating in Mexico to integrate electronic signatures (using the FIEL) into their workflow.

Through Vexbi's API, you can easily manage documents and certificates within your Vexbi account.

We have language bindings in **Shell**, **PHP**, **Ruby** and **Python**! You can view code examples on the right (switch between different programming languages using the tabs on top).

#### API Versions

All API calls are versioned, and the current Vexbi API is v1.0. We will never introduce any breaking changes within any version, but may add new, non-breaking features and enhancements from time to time.

#### Sandbox enviroment

For your convenience Vexbi offers a Sandbox environment where you can confidently test your code.

To start using the API in the **Sandbox** environment you need to first create an account at [sandbox.vexbi.com](https://sandbox.vexbi.com).

Once you have an account you will need an _APP_ID_ and an _APP_SECRET_ which you can generate in [sandbox.vexbi.com/access_tokens](https://sandbox.vexbi.com/access_tokens).

Just change the **www**.vexbi.com for **sandbox**.vexbi.com in every endpoint that you use.

<aside class="warning">The Sandbox environment is not intended to be used to sign non-test documents. Documents signed in Sandbox will not have the same legal validity as those signed in production.</aside>

#### Production enviroment

To start using the API in the **Production** environment you need to first create an account at [vexbi.com](https://www.vexbi.com).

Once you have an account you will need an _APP_ID_ and an _APP_SECRET_ which you can generate in [vexbi.com/access_tokens](https://www.vexbi.com/access_tokens).

## Vexbi-supported SDKs

We currently suppport **Ruby**, **PHP** and **Python** but are working on adding more languages.

### Ruby

```ruby
# Configure Vexbi gem
Vexbi.config do |config|
  config.app_id = '<APP_ID>'
  config.app_secret = '<APP_SECRET>'
end
```

Add this line to your application's Gemfile:

`gem 'vexbi'`

Then execute:

`$ bundle`

Or install it yourself as:

`$ gem install vexbi`

You can find the repo at [github.com/Vexbi/ruby-api-client](https://github.com/Vexbi/ruby-api-client).

### PHP

```php
<?php
// include composer autoload
require 'vendor/autoload.php';

// import Vexbi Client Class
use Vexbi\ApiClient as Vexbi;

// Configure Vexbi Library
Vexbi::setTokens('APP_ID', 'APP_SECRET');
?>
```

The best way to install Vexbi is quickly and easily with [Composer](https://getcomposer.org).

To install the most recent version, run the following command.

`php composer.phar require vexbi/api-client` 

Now your composer.json has been updated automatically and you're able to require the just created *vendor/autoload.php* file to PSR-4 autoload the library.

You can find the repo at [github.com/Vexbi/ruby-api-client](https://github.com/Vexbi/php-api-client).

### Python

```python
# Import the Client 
from vexbi import Client

# Configure Vexbi Library, you will 
# pass this to every call you make to our servers.
client = Client(app_id='APP_ID', secret_key='APP_SECRET')
# If you want to make tests without beeing charged
# you can use our sandbox enviroment with:
client.use_sandbox
```

The best way to install Vexbi lib is with [PIP](https://pypi.python.org/pypi).
To install the most recent version please run the following command.

`pip install vexbi`

You can find the repo at [github.com/Vexbi/python-api-client](https://github.com/Vexbi/python-api-client/)

## Authentication

Vexbi uses __SHA1 HMAC encryption__ to authenticate API calls. Each request has to be authenticated by following these steps:

1. A canonical string is first created using your HTTP headers containing the
content-type, content-MD5, request URI and the timestamp. You can replace content-type and content-MD5 with a blank string if needed. The timestamp must be a valid HTTP date. The canonical string is computed as follows:

`canonical_string = 'http method,content-type,content-MD5,request URI,timestamp'`

2. This string is then used to create the signature, which is a Base64 encoded
SHA1 HMAC, using the __APP_SECRET__ key.

3. This signature is then added as the `Authorization` HTTP header in the following form:

`Authorization: APIAuth APP-ID:signature-from-step-2`

```ruby
app_id = '<APP_ID>'
app_secret = '<APP_SECRET>'
rest_request = RestClient::Request.new(
  url: 'https://www.vexbi.com/api/v1/documents',
  method: :get,
)
response = ApiAuth.sign!(rest_request, app_id, app_secret).execute
json_response = JSON.load(response)
```

### Ruby Example

If you are using Ruby, we recommend using our [official gem](https://github.com/Vexbi/ruby-api-client).

If you want to create your own, you can use the [api-auth](https://github.com/mgomes/api_auth/) gem which supports many popular HTTP clients. In this example we are using the [RestClient](https://github.com/rest-client/rest-client) gem.

