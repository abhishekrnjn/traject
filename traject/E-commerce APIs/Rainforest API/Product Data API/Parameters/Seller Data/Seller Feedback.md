Seller Feedback Parameters
--------------------------

GET`/request`The Seller Feedback Parameters are applicable when making a request with `type=seller_feedback` to retrieve seller customer feedback details for a seller on Amazon - the seller is specified using the `seller_id` and `amazon_domain` parameters. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Seller feedback details are retrieved from the [feedback](https://www.amazon.com/sp?seller=A02211013Q5HP3OMSZC7W) section of the seller profile page. You can retrieve the `seller_id` value for a given seller from other Rainforest requests, such as `type=offers` requests.

A maximum of 5 seller feedback records can be returned per request. You can paginate through multiple pages of seller feedback records using the `page` parameter. Inspect the `pagination.has_next_page` property to determine whether there is a next page of results to retrieve.

![]()Seller Feedback ResultsFor example, to request `page=2` of seller feedback results for a seller with ID `A02211013Q5HP3OMSZC7W` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=seller_feedback&seller_id=A02211013Q5HP3OMSZC7W&amazon_domain=amazon.com&page=2
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="seller_feedback" \
-d seller_id="A02211013Q5HP3OMSZC7W" \
-d amazon_domain="amazon.com" \
-d page="2"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "seller_feedback",
  seller_id: "A02211013Q5HP3OMSZC7W",
  amazon_domain: "amazon.com",
  page: 2
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
  'type': 'seller_feedback',
  'seller_id': 'A02211013Q5HP3OMSZC7W',
  'amazon_domain': 'amazon.com',
  'page': '2',
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
  'type' => 'seller_feedback',
  'seller_id' => 'A02211013Q5HP3OMSZC7W',
  'amazon_domain' => 'amazon.com',
  'page' => '2'
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

Copy### Seller Feedback Parameters

The following parameters are available for all requests made when `type=seller_feedback`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve seller feedback results from for the seller specified in the seller\_id parameter. For a full list of supported Amazon domains see Supported Amazon Domains. |
| seller\_id | optional | The Amazon Seller ID to retrieve seller feedback results for. Used in combination with the amazon\_domain parameter.Note: Seller IDs can be retrieved from Rainforest API type=offers requests. |
| page | optional | The page of seller feedback results to retrieve. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Seller Feedback Results](/docs/product-data-api/results/seller-feedback)
