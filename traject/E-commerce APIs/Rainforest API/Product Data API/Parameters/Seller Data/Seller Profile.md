Seller Profile Parameters
-------------------------

GET`/request`The Seller Profile Parameters are applicable when making a request with `type=seller_profile` to retrieve seller profile details for a single seller on Amazon - the seller is specified using either the `seller_id` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon seller profile page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Seller profile details are retrieved from the [seller profile page](https://www.amazon.com/sp?seller=A02211013Q5HP3OMSZC7W) for a single seller on Amazon. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

You can use subsequent [seller products](/docs/product-data-api/parameters/seller-products) and [seller feedback](/docs/product-data-api/parameters/seller-feedback) requests to retrieve iterate all of the products and customer feedback from a given seller.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/seller_profile.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Seller Profile PageFor example, to request seller profile details for the seller with ID `A02211013Q5HP3OMSZC7W` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=seller_profile&seller_id=A02211013Q5HP3OMSZC7W&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="seller_profile" \
-d seller_id="A02211013Q5HP3OMSZC7W" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "seller_profile",
  seller_id: "A02211013Q5HP3OMSZC7W",
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
  'type': 'seller_profile',
  'seller_id': 'A02211013Q5HP3OMSZC7W',
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
  'type' => 'seller_profile',
  'asin' => 'A02211013Q5HP3OMSZC7W',
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

Copy### Seller Profile Parameters

The following parameters are available for all requests made when `type=seller_profile`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve seller profile details from for the seller specified in the seller\_id parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and seller\_id parameters are supplied then the url parameter is ignored. |
| seller\_id | optional | The Amazon Seller ID to retrieve seller profile details for. Used in combination with the amazon\_domain parameter.Note: If the seller\_id and amazon\_domain parameters are supplied then the url parameter is ignored. Note: Seller IDs can be retrieved from Rainforest API type=offers requests. |
| url | optional | The Amazon seller profile page URL of the seller to retrieve results from. |
Next Steps

* [Seller Profile Results](/docs/product-data-api/results/seller-profile)
