Getting Started
---------------

Rainforest API is an API to retrieve data from any Amazon domain worldwide in real-time. You can use Rainforest API to retrieve [products](/docs/product-data-api/parameters/product), [reviews](/docs/product-data-api/parameters/reviews), [review comments](/docs/product-data-api/parameters/review-comments), [offers](/docs/product-data-api/parameters/offers), [lightning deals](/docs/product-data-api/parameters/deals), [category results](/docs/product-data-api/parameters/category), [search results](/docs/product-data-api/parameters/search), [also-bought products](/docs/product-data-api/parameters/also-bought), [seller profiles](/docs/product-data-api/parameters/seller-profile), [seller feedback](/docs/product-data-api/parameters/seller-feedback), [seller products](/docs/product-data-api/parameters/seller-products), [reviewer profile](/docs/product-data-api/parameters/reviewer-profile), [questions](/docs/product-data-api/parameters/questions), [extended question answers](/docs/product-data-api/parameters/question-answers) and [bestselling products](/docs/product-data-api/parameters/bestsellers) from any Amazon [site](/docs/product-data-api/reference/amazon-domains).

Rainforest API executes requests in real time and returns clean, structured `JSON` or `CSV`results. You can achieve fine-grained control over your request using the [request parameters](/docs/product-data-api/parameters/common).

  
:::hint



**Lookup an ASIN by GTIN / ISBN / UPC / EAN**  
Rainforest API can automatically convert GTIN/ISBN/UPC/EAN codes to ASINs and return product data. For details of how to lookup Amazon product details by GTIN/ISBN/UPC/EAN please see refer to the [guide](/docs/product-data-api/reference/gtin-upc-ean-to-asin).  
  
Note that Rainforest will cache the GTIN-to-ASIN mapping for 2 months. To force a new GTIN lookup (for example, if you suspect the existing mapping is stale), use the `skip_gtin_cache=true` request parameter (note that using `skip_gtin_cache=true` decrements 2 credits from your balance, instead of 1).  
:::

  
:::hint



**Customer Zip & Postal Codes**  
Rainforest API allows you to set up zip or postal codes and run your requests in the context of those zipcodes. This is useful for retrieving data from highly localized ASINs such as Amazon Fresh.  
  
View the [Customer Zipcodes](/docs/zipcodes-api/overview) docs to learn more about setting up customer zipcodes on your account and using them in your requests.  
:::

### Retrieving Bestselling Products on Amazon

GET`/request`Getting Amazon data with Rainsforest API is as simple as making an HTTP `GET` request to the `request` endpoint. The only required parameters are`api_key`([sign up](https://app.rainforestapi.com/signup) for free to get an API key) and `type` (which defines the type of Amazon data you'd like to retrieve).

For example, to retrieve Bestselling products (`type=bestsellers`) for the "memory cards" Amazon Bestsellers page on amazon.com `https://www.amazon.com/s/zgbs/pc/516866` the Rainforest API request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=bestsellers&url=https://www.amazon.com/s/zgbs/pc/516866
```

```
$ curl -L --get https://api.rainforestapi.com/request \
  -d api_key="demo" \
  -d type="bestsellers" \
  -d url="https://www.amazon.com/s/zgbs/pc/516866"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "bestsellers",
  url: "https://www.amazon.com/s/zgbs/pc/516866"
}

// make the http GET request to Rainforest API
axios.get('https://api.rainforestapi.com/request', { params })
  .then(response => {

    // print the JSON response from Rainforest API
    console.log(JSON.stringify(response.data, 0, 2));

  }).catch(error => {
    // catch and print the error
    console.log(error);
  })
```

```
import requests
import json

# set up the request parameters
params = {
  'api_key': 'demo',
  'type': 'bestsellers',
  'url': 'https://www.amazon.com/s/zgbs/pc/516866'
}

# make the http GET request to Rainforest API
api_result = requests.get('https://api.rainforestapi.com/request', params)

# print the JSON response from Rainforest API
print(json.dumps(api_result.json()))
```

```
<?php
      
# set up the request parameters
$queryString = http_build_query([
  'api_key' => 'demo',
  'type' => 'bestsellers',
  'url' => 'https://www.amazon.com/s/zgbs/pc/516866'
]);

# make the http GET request to Rainforest API
$ch = curl_init(sprintf('%s?%s', 'https://api.rainforestapi.com/request', $queryString));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
# the following options are required if you're using an outdated OpenSSL version
# more details: https://www.openssl.org/blog/blog/2021/09/13/LetsEncryptRootCertExpire/
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
curl_setopt($ch, CURLOPT_TIMEOUT, 180);

$api_result = curl_exec($ch);

curl_close($ch);

# print the JSON response from Rainforest API
echo $api_result;

?>
```
  
:::::

Copy[Open in Tab](https://api.rainforestapi.com/request?api_key=demo&type=bestsellers&url=https://www.amazon.com/s/zgbs/pc/516866)  
:::hint



To view Rainforest API JSON results clearly in your browser we recommend these extensions for [Chrome](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc) and [Firefox](https://addons.mozilla.org/en-GB/firefox/addon/jsonview/)  
:::

The results of the Bestsellers request are shown below, the bestselling products are within the `bestsellers` array. For full documentation on Bestsellers results see the [Bestsellers Results](/docs/product-data-api/results/bestsellers) docs.

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"bestsellers":[...]"pagination":{...}"bestsellers\_info":{...}}Copy  
:::hint



**Response Times & Concurrency**  
Rainforest API gathers data from Amazon in real-time and will typically return a result in 1-6 seconds. Please inspect the [HTTP Response Code](/docs/response-codes) and update your app accordingly.  
  
If you need to run large volumes of requests consider using the [Collections API](/docs/collections-api). Collections allow you to enqueue up to 15,000 requests, run them manually or on a schedule and execute them concurrently on Rainforest API's infrastructure.  
:::

### Getting Data for an Individual Product

GET`/request`Lets say we want to change our query to request a different type of data - information on a specific [product](/docs/product-data-api/parameters/product), in this case the ASIN (Amazon product identifier) `B000YDDF6O` on `amazon.com`. Here's the Rainforest API request to achieve that:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=product&asin=B000YDDF6O&amazon_domain=amazon.com
```

```
$ curl -L --get https://api.rainforestapi.com/request \
  -d api_key="demo" \
  -d type="product" \
  -d asin="B000YDDF6O" \
  -d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "product",
  asin: "B000YDDF6O",
  amazon_domain: "amazon.com"
}

// make the http GET request to Rainforest API
axios.get('https://api.rainforestapi.com/request', { params })
  .then(response => {

    // print the JSON response from Rainforest API
    console.log(JSON.stringify(response.data, 0, 2));

  }).catch(error => {
    // catch and print the error
    console.log(error);
  })
```

```
import requests
import json

# set up the request parameters
params = {
  'api_key': 'demo',
  'type': 'product',
  'asin': 'B000YDDF6O',
  'amazon_domain': 'amazon.com'
}

# make the http GET request to Rainforest API
api_result = requests.get('https://api.rainforestapi.com/request', params)

# print the JSON response from Rainforest API
print(json.dumps(api_result.json()))
```

```
<?php
      
# set up the request parameters
$queryString = http_build_query([
  'api_key' => 'demo',
  'type': 'product',
  'asin': 'B000YDDF6O',
  'amazon_domain': 'amazon.com'
]);

# make the http GET request to Rainforest API
$ch = curl_init(sprintf('%s?%s', 'https://api.rainforestapi.com/request', $queryString));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
# the following options are required if you're using an outdated OpenSSL version
# more details: https://www.openssl.org/blog/blog/2021/09/13/LetsEncryptRootCertExpire/
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
curl_setopt($ch, CURLOPT_TIMEOUT, 180);

$api_result = curl_exec($ch);
curl_close($ch);

# print the JSON response from Rainforest API
echo $api_result;

?>
```
  
:::::

Copy[Open in Tab](https://api.rainforestapi.com/request?api_key=demo&type=product&asin=B000YDDF6O&amazon_domain=amazon.com)The result of the Product request is shown below. For full documentation on Product results see the [Product Results](/docs/product-data-api/results/product) docs.

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"product":{...}"frequently\_bought\_together":{...}"also\_viewed":[...]"sponsored\_products":[...]}CopyNext Steps

* [Searching for Products on Amazon](/docs/product-data-api/parameters/search)
* [Retrieving Amazon Customer Reviews](/docs/product-data-api/parameters/reviews)
* [Retrieving Product Offers](/docs/product-data-api/parameters/offers)
