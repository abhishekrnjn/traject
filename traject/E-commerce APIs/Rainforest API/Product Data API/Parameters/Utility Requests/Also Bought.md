Also Bought Parameters
----------------------

GET`/request`The Also Bought Parameters are applicable when making a request with `type=also_bought` to retrieve also bought details for a single product on Amazon - the product is specified using either the `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon product page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Also bought details are retrieved from the [product page](https://www.amazon.com/dp/B084ZF5D65) for a single product on Amazon. An `type=also_bought` request will automatically paginate through all of the pages of also-bought data and return every also bought result.

![]()Also Bought SectionFor example, to request also bought details for the ASIN `B084ZF5D65` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=also_bought&asin=B084ZF5D65&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="also_bought" \
-d asin="B084ZF5D65" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "also_bought",
  asin: "B084ZF5D65",
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
  'type': 'also_bought',
  'asin': 'B084ZF5D65',
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
  'type' => 'also_bought',
  'asin' => 'B084ZF5D65',
  'amazon_domain' => 'amazon.com'
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

Copy### Also Bought Parameters

The following parameters are available for all requests made when `type=also_bought`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve also bought details from for the product specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon ASIN (product ID) to retrieve also bought details for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| url | optional | The Amazon product page URL to retrieve also bought results from. |
Next Steps

* [Also Bought Results](/docs/product-data-api/results/also-bought)
