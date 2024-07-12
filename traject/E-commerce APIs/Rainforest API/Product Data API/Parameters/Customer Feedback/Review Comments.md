Review Comments Parameters
--------------------------

GET`/request`The Review Comments Parameters are applicable when making a request with `type=review_comments` to retrieve customer Review Comments for a single customer review on Amazon - the review is specified using the `review_id`, `asin` and `amazon_domain` parameters. The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Review comments are retrieved from the [customer reviews page](https://www.amazon.com/product-reviews/B073JYC4XM) for a single customer review for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/review_comments.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Review Comments Section  
:::hint



**Retrieving Review IDs**  
To make a `type=review_comments` request you must provide a `review_id`. Review IDs are retrieved by making `type=reviews` requests to retrieve reviews for a given product. See the [Reviews Parameters](/docs/product-data-api/parameters/reviews) documentation for more information.  
:::

  
:::hint



**Review Comments Count**  
Rainforest can retrieve up to 100 review comments per request. For tracking new comments the most common approach is to run a `type=review_comments` request with `sort_by=most_recent` set, to ensure you always retrieve the latest review comments.  
:::

For example, to request review comments, sorted by `most_recent`, for the Review ID `RKXA6MFEZGGSY` of ASIN `B07H9J1YXN` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=review_comments&amazon_domain=amazon.com&asin=B07H9J1YXN&review_id=RKXA6MFEZGGSY&sort_by=most_recent
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="review_comments" \
-d amazon_domain="amazon.com" \ 
-d asin="B07H9J1YXN" \
-d review_id="RKXA6MFEZGGSY" \ 
-d sort_by="most_recent"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "review_comments",
  amazon_domain: "amazon.com",
  asin: "B07H9J1YXN",
  review_id: "RKXA6MFEZGGSY",
  sort_by: "most_recent"
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
  'type': 'review_comments',
  'amazon_domain': 'amazon.com',
  'asin': 'B07H9J1YXN',
  'review_id': 'RKXA6MFEZGGSY',
  'sort_by': 'most_recent'
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
  'type' => 'review_comments',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B07H9J1YXN',
  'review_id' => 'RKXA6MFEZGGSY',
  'sort_by' => 'most_recent'
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

Copy### Review Comments Parameters

The following parameters are available for all requests made when `type=review_comments`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | required | The Amazon domain to retrieve Review Comments for the Review ID specified in the review\_id parameter and ASIN specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains. Used in combination with the asin and review\_id parameters. |
| asin | required | The Amazon ASIN to retrieve Review Comments for. Used in combination with the amazon\_domain and review\_id parameters. |
| review\_id | required | The Review ID, as returned by a type=reviews request, to retrieve Review Comments for. Used in combination with the amazon\_domain and asin parameters. |
| sort\_by | optional | An optional sort order for the returned review comments. Valid values are most\_recent and oldest |
Next Steps

* [Review Comments Results](/docs/product-data-api/results/review-comments)
