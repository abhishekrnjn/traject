Shop By Look Parameters
-----------------------

GET`/request`The Shop By Look Bought Parameters are applicable when making a request with `type=shop_by_look` to retrieve Shop By Look ASINs for a single product on Amazon - the product is specified using the `asin` request parameter.

Shop By Look details are retrieved from the [product page](https://www.amazon.de/dp/B087CLWH69) for a single product on Amazon. An `type=shop_by_look`. The first page of Shop By Look results are always returned with `type=product` requests (to the product page). The purpose of the dedicated `type=shop_by_look` request is to allow pagination through all pages of Shop By Look results.

**Note** that the 1st ASIN returned by a Shop By Look request is always the original ASIN specified in the `asin` request parameter. A maximum of 12 Shop By Look ASINs are returned per request.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/shop_by_look.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Shop By Look SectionFor example, to request Shop By Look ASINs for the ASIN `B087CLWH69` on `amazon.de` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=shop_by_look&asin=B087CLWH69&amazon_domain=amazon.de
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="shop_by_look" \
-d asin="B087CLWH69" \
-d amazon_domain="amazon.de"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "shop_by_look",
  asin: "B087CLWH69",
  amazon_domain: "amazon.de"
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
  'type': 'shop_by_look',
  'asin': 'B087CLWH69',
  'amazon_domain': 'amazon.de'
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
  'type' => 'shop_by_look',
  'asin' => 'B087CLWH69',
  'amazon_domain' => 'amazon.de'
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

Copy### Shop By Look Parameters

The following parameters are available for all requests made when `type=shop_by_look`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | required | The Amazon domain to retrieve Shop By Look ASINs from for the product specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| asin | required | The Amazon ASIN (product ID) to retrieve Shop By Look ASINs for. Used in combination with the amazon\_domain parameter. |
| page | optional | The page of Shop By Look results to retrieve. If not specified defaults to 1. Note that a maximum of 12 results are returned per page. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Shop By Look Results](/docs/product-data-api/results/shop-by-look)
