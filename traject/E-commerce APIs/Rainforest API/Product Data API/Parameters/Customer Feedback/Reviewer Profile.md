Reviewer Profile Parameters
---------------------------

GET`/request`When making a request with the `type` [parameter](/docs/product-data-api/parameters/reviewer-profile) set to `type=reviewer_profile` Rainforest API will return details of reviewer specified in either the `reviewer_id` and `amazon_domain` parameters or the `url` parameter.

Reviewer profile details are retrieved from the [reviewer profile page](https://www.amazon.com/gp/profile/amzn1.account.AHBEI6Q4F4WHRIFK5CWQMRVPOQMA). You can retrieve the `reviewer_id` value for a given reviewer from other Rainforest requests, such as `type=reviews` requests.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/reviewer_profile.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Reviewer Profile PageFor example, to request reviewer profile details for the reviewer with ID `AHBEI6Q4F4WHRIFK5CWQMRVPOQMA` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=reviewer_profile&reviewer_id=AHBEI6Q4F4WHRIFK5CWQMRVPOQMA&amazon_domain=amazon.com
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="reviewer_profile" \
-d reviewer_id="AHBEI6Q4F4WHRIFK5CWQMRVPOQMA" \
-d amazon_domain="amazon.com"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "reviewer_profile",
  reviewer_id: "AHBEI6Q4F4WHRIFK5CWQMRVPOQMA",
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
  'type': 'reviewer_profile',
  'reviewer_id': 'AHBEI6Q4F4WHRIFK5CWQMRVPOQMA',
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
  'type' => 'reviewer_profile',
  'asin' => 'AHBEI6Q4F4WHRIFK5CWQMRVPOQMA',
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

Copy### Reviewer Profile Parameters

The following parameters are available for all requests made when `type=reviewer_profile`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve reviewer profile details from for the reviewer specified in the reviewer\_id parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and reviewer\_id parameters are supplied then the url parameter is ignored. |
| reviewer\_id | optional | The Amazon Reviewer ID to retrieve reviewer profile details for. Used in combination with the amazon\_domain parameter.Note: If the reviewer\_id and amazon\_domain parameters are supplied then the url parameter is ignored. Reviewer IDs can be retrieved from other Rainforest API requests, for example type=reviews requests. |
| url | optional | The Amazon reviewer profile page URL of the reviewer to retrieve results from. |
| reviewer\_profile\_pages | optional | The number of pages of reviews to retrieve from the reviewer profile page when type=reviewer\_profile.This parameter is different from the more usual page parameter as pagination of reviewer profile reviews is performed from an infinate-scrolling list.It is not possible to "go to page 3", so the reviewer\_profile\_pages allows you retrieve "the first X" pages of reviews (a maximum of 10 reviews are returned per page).Note: that using reviewer\_profile\_pages decrements a credit for each page of reviews retrieved, for example, reviewer\_profile\_pages=3 would decrement 3 credits from your balance. |
Next Steps

* [Reviewer Profile Results](/docs/product-data-api/results/reviewer-profile)
