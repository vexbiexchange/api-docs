# Introduction

Welcome to the Vexbi API! We at Vexbi provide a simple and robust RESTful API to integrate orders booking into your workflow.

At this time, we have language bindings for **Python** with more to come! You can view code examples on the right.

#### API Versions

All API calls are versioned, and the current Vexbi API is v1.0. We will never introduce any breaking changes within any version, but may add new, non-breaking features and enhancements from time to time.

<!-- #### Sandbox environment

For your convenience Vexbi offers a Sandbox environment where you can confidently test your code.

To start using the API in the **Sandbox** environment you need to first create an account at [sandbox.vexbi.com](https://sandbox.vexbi.com).

Once you have an account you will need an _APP_ID_ and an _APP_SECRET_ which you can generate in [sandbox.vexbi.com/access_tokens](https://sandbox.vexbi.com/authentications).

Just change the **www**.vexbi.com for **sandbox**.vexbi.com in every endpoint that you use.

<aside class="warning">The Sandbox environment is not intended to be used to create real world orders. Orders booked in Sandbox will be using testnet networks only.</aside> -->

#### Production environment

To start using the API in the **Production** environment you need to first create an account at [vexbi.com](https://www.vexbi.com).

Once you have an account you will need an _APP_ID_ and an _APP_SECRET_ which you can generate in [vexbi.com/authentications](https://www.vexbi.com/authentications).

## Vexbi-supported SDKs

We currently suppport **Python** but are working on adding more languages.

### Python

```python
# Import the Client 
from vexbi import Client

# Configure Vexbi Library, you will 
# pass this to every call you make to our servers.
client = Client(app_id='APP_ID', secret_key='APP_SECRET')
```

The best way to install Vexbi lib is with [PIP](https://pypi.python.org/pypi).
To install the most recent version please run the following command.

`pip install vexbi`

You can find the repo at [github.com/Vexbi/python-api-client](https://github.com/Vexbi/python-api-client/)

## Authentication

When not using a supported Vexbi SDK, you need to authenticate manually to submit API calls. Vexbi uses __SHA1 HMAC encryption__ to authenticate API calls. Each request has to be authenticated by following these steps:

1. A canonical string is first created using your HTTP headers containing the
content-type, content-MD5, request URI and the timestamp. You can replace content-type and content-MD5 with a blank string if needed. The timestamp must be a valid HTTP date. The canonical string is computed as follows:

`canonical_string = 'http method,content-type,content-MD5,request URI,timestamp'`

2. This string is then used to create the signature, which is a Base64 encoded
SHA1 HMAC, using the __APP_SECRET__ key.

3. This signature is then added as the `Authorization` HTTP header in the following form:

`Authorization: APIAuth APP-ID:signature-from-step-2`

<!-- ```ruby
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

If you want to create your own, you can use the [api-auth](https://github.com/mgomes/api_auth/) gem which supports many popular HTTP clients. In this example we are using the [RestClient](https://github.com/rest-client/rest-client) gem. -->

