ASIN to GTIN Parameters
-----------------------

GET`/request`When making a request with the `type` parameter set to `type=asin_to_gtin` Rainforest API will attempt to look up GTIN / EAN / UPC / ISBN numbers for the ASIN and Amazon domain specified in the `asin` and `amazon_domain` parameters.

  
:::hint



GTIN / EAN / UPC / ISBN values are retrieved from public domain sources (as they are not published by Amazon themselves).  
:::

For example, to request ASIN to GTIN results for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=asin_to_gtin&asin=B073JYC4XM&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="asin_to_gtin" \
-d asin="B073JYC4XM" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "asin_to_gtin",
  asin: "B073JYC4XM",
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
  'type': 'asin_to_gtin',
  'asin': 'B073JYC4XM',
  'amazon_domain': 'amazon.com',
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
  'type' => 'asin_to_gtin',
  'asin' => 'B073JYC4XM',
  'amazon_domain' => 'amazon.com',
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

Copy### ASIN to GTIN Parameters

The following parameters are available for all requests made when `type=asin_to_gtin`.

| Parameter | Required | Description |
| --- | --- | --- |
| asin | required | The Amazon ASIN (product ID) to retrieve GTIN(s) for. Used in combination with the amazon\_domain parameter. |
| amazon\_domain | required | The Amazon domain to retrieve ASIN to GTIN details from for the ASIN specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| skip\_gtin\_cache | optional | If you suspect Rainforest API's GTIN / UPC / EAN / ISBN results to be stale (by default results are cached by the API for up to 2 months) you can request a fresh public-domain lookup of GTIN / UPC / EAN / ISBN values be performed by setting the skip\_gtin\_cache=true request parameter (note that using skip\_gtin\_cache=true decrements 2 credits from your balance, instead of 1). |
Next Steps

* [ASIN to GTIN Results](/docs/product-data-api/results/asin-to-gtin)
