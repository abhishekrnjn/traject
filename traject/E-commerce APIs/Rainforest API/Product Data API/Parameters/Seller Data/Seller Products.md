Seller Products Parameters
--------------------------

GET`/request`The Seller Products Parameters are applicable when making a request with `type=seller_products` to retrieve seller product listing results for a single seller on Amazon - the seller is specified using either the `seller_id` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon seller product listing page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Seller product listing results are retrieved from the [seller product listings page](https://www.amazon.com/s?me=A02211013Q5HP3OMSZC7W&marketplaceID=ATVPDKIKX0DER) for a single seller on Amazon. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

![]()Seller Products Listing PageFor example, to request seller product listings for the seller with ID `A02211013Q5HP3OMSZC7W` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=seller_products&seller_id=A02211013Q5HP3OMSZC7W&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="seller_products" \
-d seller_id="A02211013Q5HP3OMSZC7W" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "seller_products",
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
  'type': 'seller_products',
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
  'type' => 'seller_products',
  'seller_id' => 'A02211013Q5HP3OMSZC7W',
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

Copy### Seller Products Parameters

The following parameters are available for all requests made when `type=seller_products`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve seller product listings from for the seller specified in the seller\_id parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and seller\_id parameters are supplied then the url parameter is ignored. |
| seller\_id | optional | The Amazon Seller ID to retrieve seller product listings for. Used in combination with the amazon\_domain parameter.Note: If the seller\_id and amazon\_domain parameters are supplied then the url parameter is ignored. Note: Seller IDs can be retrieved from Rainforest API type=offers requests. |
| refinements | optional | A comma-seperated list of refinement values to filter the seller product results by. These allow you to refine your request by values such as "Reviews rating 4 and over", "price range" and "brand".Refinement values are returned in the refinements array of each type=seller\_products result (if they are displayed). Refinement values are dynamic and change by seller. If you wish to use refinements you should first issue a type=seller\_products request without specifying any refinements to retrieve a master list of the avaialble refinements for the given request. You can then cache these refinement values for use on subsequent requests.For example, to run a type=seller\_products request specifying two refinements with values p\_85/2470955011 and p\_36/2421886011 the value of the refinements parameter would be refinements=p\_85/2470955011,p\_36/2421886011 |
| url | optional | The Amazon seller products listing page URL to retrieve seller products results from. |
| page | optional | The page of seller products results to retrieve. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Seller Products Results](/docs/product-data-api/results/seller-products)
