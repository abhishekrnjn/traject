Wishlist Parameters
-------------------

GET`/request`The Wishlist Parameters are applicable when making a request with the `type` [parameter](/docs/product-data-api/parameters/wishlist) set to `type=wishlist` Rainforest API will return data from the Wishlist page for the wishlist specified in either the `wishlist_id` and `amazon_domain` parameters or the `url` parameter. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Wishlist data is retrieved from the [Wishlist popup](https://www.amazon.com/hz/wishlist/ls/38B3V3AT7UH9B).

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/wishlist.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Wishlist Page  
:::hint



**Paginating Results**  
Amazon returns 10 Wishlist per page. To request more wishlist results issue additional requests passing the `next_page_token` parameter from the previous request.  
  
**Note** due to the infinate-scrolling behaviour of wishlist pages, you cannot reference a specific page directly. Pagination is achieved via the `next_page_token` request parameter.  
:::

For example, to request wishlist results for the wishlist ID `38B3V3AT7UH9B` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=wishlist&amazon_domain=amazon.com&wishlist_id=38B3V3AT7UH9B
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="wishlist" \
-d amazon_domain="amazon.com" \ 
-d wishlist_id="38B3V3AT7UH9B"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "wishlist",
  amazon_domain: "amazon.com",
  wishlist_id: "38B3V3AT7UH9B"
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
  'type': 'wishlist',
  'amazon_domain': 'amazon.com',
  'wishlist_id': '38B3V3AT7UH9B'
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
  'type' => 'wishlist',
  'amazon_domain' => 'amazon.com',
  'wishlist_id' => '38B3V3AT7UH9B'
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

Copy### Wishlist Parameters

The following parameters are available for all requests made when `type=wishlist`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve Wishlist for the product specified in the asin parameter from. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| wishlist\_id | optional | The Amazon wishlist ID to retrieve Wishlist results for. Used in combination with the amazon\_domain parameter. The wishlist ID can be found in any Amazon wishlist URL after the /ls/ component of the wishlist URL.Note: If the wishlist\_id and amazon\_domain parameters are supplied then the url parameter is ignored. |
| url | optional | The Amazon wishlist-page URL to retrieve Wishlist results from.Note: If the url parameter is supplied then the amazon\_domain and wishlist\_url parameters are ignored. |
| sort\_by | optional | Determines the sort order of wishlist items to return. Omit the sort\_by parameter to return results in the default sort order. Valid values are:price\_high\_to\_lowReturns highest priced wishlist items first.price\_low\_to\_highReturns lowest priced wishlist items first.priority\_high\_to\_lowReturns highest priority wishlist items first. |
| next\_page\_token | optional | The current page of Wishlist results to retrieve. Inspect the pagination.next\_page\_token property in the Wishlist results to retrieve the next\_page\_token of the subsequent page. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Wishlist Results](/docs/product-data-api/results/wishlist)
