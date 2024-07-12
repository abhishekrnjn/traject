Store Parameters
----------------

GET`/request`The Store parameters are applicable when making a request with `type=store` to retrieve Brand Store results for a Brand Store. The Brand Store can be specified either by the `url` parameter, or by a combination of the `store_id` and `amazon_domain` parameters. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

  
:::hint



**Brand Store IDs and URLs**  
Brand Store IDs and URLs are returned by `type=product` [product page](/docs/product-data-api/results/product) requests under the `brand_store.id` and `brand_store.url` properties assuming they are shown on the product page. The Brand Store ID/URL is typically shown above the ASIN title, as shown below:  
  
![]()  
:::

Brand Store results are retrieved from the [brand store page](https://www.amazon.com/stores/page/70F3122D-4966-4242-A8A6-871C8D7E6F8B) on Amazon.

![]()Brand Store PageFor example, to request Brand Store results for the Store ID `70F3122D-4966-4242-A8A6-871C8D7E6F8B` on `amazon.com`, the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=store&store_id=70F3122D-4966-4242-A8A6-871C8D7E6F8B&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="store" \
-d store_id="70F3122D-4966-4242-A8A6-871C8D7E6F8B" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "store",
  store_id: "70F3122D-4966-4242-A8A6-871C8D7E6F8B",
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
  'type': 'store',
  'store_id': '70F3122D-4966-4242-A8A6-871C8D7E6F8B',
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
  'type' => 'store',
  'store_id' => '70F3122D-4966-4242-A8A6-871C8D7E6F8B',
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

Copy### Store Parameters

The following parameters are available for all requests made when `type=store`.

| Parameter | Required | Description |
| --- | --- | --- |
| store\_id | optional | A Brand Store ID to retrieve results from. Should be used in combination with the amazon\_domain parameter.Note if the url parameter is supplied then the store\_id parameter is ignored as the url itself specifies the store ID. |
| amazon\_domain | optional | The Amazon domain to retrieve Brand Store results from. For a full list of supported Amazon domains see Supported Amazon Domains. Should be used in combination with the store\_id parameter.Note if the url parameter is supplied then the amazon\_domain parameter is ignored as the url itself specifies the Amazon domain. |
| url | optional | The Brand Store page URL to retrieve Brand Store results from. Be sure to URL-encode the url parameter.Note the url parameter is supplied, the store\_id and amazon\_domain parameters cannot be used (as the url itself defines the Store ID and Amazon domain used). |
| page | optional | The current page of Brand Store results to retrieve. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Store Results](/docs/product-data-api/results/store)
