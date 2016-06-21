---
title: Blockchain API

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/blockchain/service-my-wallet-v3' target="_blank">Check out our wallet API module</a>

search: true
---

# Introduction

The [Blockchain](https://www.blockchain.com/) API will allow you to send & receive bitcoin, query JSON data on blocks and transactions, and get information regarding the blockchain. **Almost all functionality and data you see on this website is available through API calls.**

Blockchain.info provides official API libraries for <a href="https://github.com/blockchain/api-v1-client-python" target="_blank_"> Python</a>, <a href="https://github.com/blockchain/api-v1-client-java" target="_blank_"> Java</a>, <a href="https://github.com/blockchain/api-v1-client-csharp" target="_blank_"> .NET (C#)</a>, <a href="https://github.com/blockchain/api-v1-client-ruby" target="_blank_"> Ruby</a>, <a href="https://github.com/blockchain/api-v1-client-node" target="_blank_"> Node</a>, and <a href="https://github.com/blockchain/api-v1-client-php" target="_blank_"> PHP</a>.

# API Keys

For a **recieve payments v2 only** key, please apply for a key <a href="https://api.blockchain.info/v2/apikey/request/" target="_blank_">here</a>.

For **blockchain wallet services and increased blockchain data limits**, please apply for a key <a href="https://blockchain.info/api/api_create_code" target="_blank_">here</a>.

<aside class="notice">
You cannot use the keys interchangeably.
</aside>

# Simple Address Lookups

Simple plain text API for querying blockchain data, usually one number. For more complex needs, please see our Detailed Bitcoin Data section.

All bitcoin values are in <a href="http://www.btcsatoshi.com/" target="_blank_">Satoshi</a> i.e. divide by 100,000,000 to get the amount in BTC.

## Address Balance

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/addressbalance/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/addressbalance/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/addressbalance/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/addressbalance/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>2000000


Get the total number of bitcoins received by an address (in <a href="http://www.btcsatoshi.com/" target="_blank_">satoshi</a>. Multiple addresses separated by a pipe: |

<aside class="warning">Do not use to process payments without the confirmations parameter.</aside>

### HTTP Request

`GET https://blockchain.info/q/addressbalance/`<span id="param">address</span>`?confirmations=`<span id="param">0</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
address | yes | Bitcoin address to query for current bitcoin balance.
confirmations | no | Number of confirmations required for a transaction to be included in response.

## Total Received

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/getreceivedbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/getreceivedbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/getreceivedbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/getreceivedbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>2000000


Get the current balance of an address (in <a href="http://www.btcsatoshi.com/" target="_blank_">satoshi</a>). Multiple addresses separated by a pipe: |

<aside class="warning">This may be a different value than 'balance'.</aside>

### HTTP Request

`GET https://blockchain.info/q/getreceivedbyaddress/`<span id="param">address</span>`?confirmations=`<span id="param">0</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
address | yes | Bitcoin address to query for current bitcoin balance.
confirmations | no | Number of confirmations required for a transaction to be included in response.

## Total Sent

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/getsentbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/getsentbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/getsentbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/getsentbyaddress/1EzwoHtiXB4iFwedPr49iywjZn2nnekhoj?confirmations=3', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>2000000


Get the total number of bitcoins sent by an address (in <a href="http://www.btcsatoshi.com/" target="_blank_">satoshi</a>. Multiple addresses separated by a pipe: |


### HTTP Request

`GET https://blockchain.info/q/getsentbyaddress/`<span id="param">address</span>`?confirmations=`<span id="param">0</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
address | yes | Bitcoin address to query for current bitcoin balance.
confirmations | no | Number of confirmations required for a transaction to be included in response.











# Simple Real-Time Data

Simple plain text API for querying blockchain data, usually one number. For more complex needs, please see Bitcoin Data API.

All bitcoin values are in <a href="http://www.btcsatoshi.com/" target="_blank_">Satoshi</a> i.e. divide by 100,000,000 to get the amount in BTC.

## Mining Difficulty

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/getdifficulty'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/getdifficulty')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/getdifficulty"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/getdifficulty', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>46684376316.86029


Current difficulty target as decimal number

### HTTP Request

`GET https://blockchain.info/q/getdifficulty`


## Block Count

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/getblockcount'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/getblockcount')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/getblockcount"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/getblockcount', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>346322


Current block height in the longest chain

### HTTP Request

`GET https://blockchain.info/q/getblockcount`

## Latest Hash

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/latesthash'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/latesthash')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/latesthash"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/latesthash', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 000000000000000003ecdd4d0b36d9f2c718dcae8f202191076b42e994cca5aa


Hash of the latest block

### HTTP Request

`GET https://blockchain.info/q/latesthash`

## Bitcoin Per Block

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/bcperblock'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/bcperblock')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/bcperblock"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/bcperblock', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 2500000000


Current block reward in BTC

### HTTP Request

`GET https://blockchain.info/q/bcperblock`

## Bitcoin Per Block

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/totalbc'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/totalbc')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/totalbc"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/totalbc', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 2500000000


Total bitcoins in circulation (delayed up to 1 hour)

### HTTP Request

`GET https://blockchain.info/q/totalbc`

## Bitcoin Per Block

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/probability'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/probability')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/probability"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/probability', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 4.987335421888922e-21


Probability of finding a valid block each hash attempt

### HTTP Request

`GET https://blockchain.info/q/probability`

## Hashes to Win

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/hashestowin'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/hashestowin')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/hashestowin"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/hashestowin', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 9223372036854776000


Average number of hash attempts needed to solve a block

### HTTP Request

`GET https://blockchain.info/q/hashestowin`

## Next Re-Target

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/nextretarget'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/nextretarget')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/nextretarget"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/nextretarget', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 346751


Block height of the next difficulty re-target

### HTTP Request

`GET https://blockchain.info/q/nextretarget`

## Average Transaction Size

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/avgtxsize/200'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/avgtxsize/200')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/avgtxsize/200"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/avgtxsize/200', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>530


Average transaction size in Bytes. Default is the past 1000 blocks.


### HTTP Request

`GET https://blockchain.info/q/avgtxsize/`<span id="param">2000</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
number | no | Number of past blocks to include

## Average Transaction Value

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/avgtxvalue/200'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/avgtxvalue/200')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/avgtxvalue/200"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/avgtxvalue/200', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

>530


Average transaction value. Default is the past 1000 transactions.


### HTTP Request

`GET https://blockchain.info/q/avgtxvalue/`<span id="param">2000</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
number | no | Number of past transactions to include

## Average Transaction Number

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/avgtxnumber/200'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/avgtxnumber/200')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/avgtxnumber/200"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/avgtxnumber/200', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 787


Average number of transactions per block. Default is past 100 blocks.


### HTTP Request

`GET https://blockchain.info/q/avgtxnumber/`<span id="param">200</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
number | no | Number of past blocks to include

## Block Interval

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/interval'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/interval')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/interval"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/interval', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 691.1999999999999


Average time between blocks in seconds

### HTTP Request

`GET https://blockchain.info/q/interval`

## ETA

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/eta'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/eta')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/eta"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/eta', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 691.1999999999999


Average time between blocks in seconds

### HTTP Request

`GET https://blockchain.info/q/eta`

## Unconfirmed Transactions

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/unconfirmedcount'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/unconfirmedcount')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/unconfirmedcount"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/unconfirmedcount', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 3285


Number of pending unconfirmed transactions.

### HTTP Request

`GET https://blockchain.info/q/unconfirmedcount`

## Market Cap

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/marketcap'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/marketcap')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/marketcap"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/marketcap', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 3797652611.75


USD market cap based on 24 hour weighted price.

### HTTP Request

`GET https://blockchain.info/q/marketcap`

## 24hr Price

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/24hrprice'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/24hrprice')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/24hrprice"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/24hrprice', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 3797652611.75


24 hour weighted price from the largest exchanges.

### HTTP Request

`GET https://blockchain.info/q/24hrprice`

## 24hr Transactions

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/24hrtransactioncount'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/24hrtransactioncount')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/24hrtransactioncount"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/24hrtransactioncount', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 92895


Number of transactions in the past 24 hours.

### HTTP Request

`GET https://blockchain.info/q/24hrtransactioncount`

## 24hr Volume

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/24hrbtcsent'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/24hrbtcsent')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/24hrbtcsent"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/24hrbtcsent', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 92895


Number of bitcoin sent in the last 24 hours (in in <a href="http://www.btcsatoshi.com/" target="_blank_">Satoshi</a>)

### HTTP Request

`GET https://blockchain.info/q/24hrbtcsent`

## Hash Rate

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/hashrate'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/hashrate')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/hashrate"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/hashrate', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> 352745325.9987376


Estimated network hash rate in Gigahashes per second.

### HTTP Request

`GET https://blockchain.info/q/hashrate`

## Rejected

```ruby
require 'rest_client'

response = RestClient.get 'https://blockchain.info/q/rejected/200'
puts response
```

```python
from urllib2 import Request, urlopen

request = Request('https://blockchain.info/q/rejected/200')

response_body = urlopen(request).read()
print response_body
```

```shell
curl "https://blockchain.info/q/rejected/200"
```

```javascript
var request = require('request');

request('https://blockchain.info/q/rejected/200', function (error, response, body) {
  console.log('Status:', response.statusCode);
  console.log('Headers:', JSON.stringify(response.headers));
  console.log('Response:', body);
});
```

```
The above command returns a text response:
```

> The Maximum number of outputs in a single transaction is 200


Lookup the reason why the provided transaction or block hash was rejected (if any). <a href="https://blockchain.info/rejected" target="_blank_">Please see our page here for an example.</a>


### HTTP Request

`GET https://blockchain.info/q/rejected/`<span id="param">2000</span>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
number | no | Number of past blocks to include
