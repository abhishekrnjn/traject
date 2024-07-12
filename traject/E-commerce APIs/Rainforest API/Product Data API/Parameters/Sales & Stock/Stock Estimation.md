Stock Estimation Parameters
---------------------------

GET`/request`The Stock Estimation Parameters are applicable when making a request with `type=stock_estimation` to retrieve stock level and related information from the shopping cart for a single product on Amazon - the product is specified using the `asin` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Stock level data is retrieved from the shopping cart page for a single product on Amazon.

  
:::hint



**Stock for a Specific Seller Offer**  
By default a Stock Estimation request will return data for the **buybox winning offer** for the passed ASIN.  
  
To return stock estimation for a specific seller offer, rather than the buybox winner, you should pass the `offer_id`, retrieved from a `type=offers` [offers](/docs/product-data-api/parameters/offers) request, in the stock estimation request's `offer_id` parameter.  
Note that `offer_id`'s are dynamic, and change over time, so it is recommended that you run your `type=offers` request to retrieve the `offer_id` directly before your stock estimation request.  
:::

  
:::hint



**Products that Require Login**  
For some ASINs Amazon will require the user to be logged in to their Amazon account to add the product to the cart.  
  
In these instances Rainforest will be unable to provide stock estimation data. You can determine whether this is the case by inspecting the `stock_estimation.requires_login = true` property of the response.  
:::

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/stock_estimation.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Stock Estimation PageFor example to request stock-estimation data for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=stock_estimation&amazon_domain=amazon.com&asin=B073JYC4XM
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="stock_estimation" \
-d amazon_domain="amazon.com" \
-d asin="B073JYC4XM"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "stock_estimation",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM"
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
  'type': 'stock_estimation',
  'amazon_domain': 'amazon.com',
  'asin': 'B073JYC4XM'
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
  'type' => 'stock_estimation',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B073JYC4XM'
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

Copy### Stock Estimation Parameters

The following parameters are available for all requests made when `type=stock_estimation`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain on which to perform the stock estimation for the product specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| asin | optional | The Amazon ASIN (product ID) to perform the stock estimation on. Used in combination with the amazon\_domain parameter. |
| offer\_id | optional | By default a Stock Estimation request will return data for the buybox winning offer for the passed ASIN.To return stock estimation for a specific seller offer, rather than the buybox winner, you should pass the offer\_id, retrieved from a type=offers offers request, in the stock estimation request's offer\_id parameter.Note that offer\_id's are dynamic, and change over time, so it is recommended that you run your type=offers request to retrieve the offer\_id directly before your stock estimation request. |
Next Steps

* [Stock Estimation Results](/docs/product-data-api/results/stock-estimation)
