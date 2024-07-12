Author Page Parameters
----------------------

GET`/request`The Author Page Parameters are applicable when making a request with `type=author_page` to retrieve data from the authors page single author on Amazon - the author is specified using either the author `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon authors page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Author Page data is retrieved from the [author page](https://www.amazon.com/kindle-dbs/entity/author/B000APVZ7W) for a single author on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/authors_page.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Author PageFor example, to request data from the authors page for the author-ASIN `B000APVZ7W` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=author_page&amazon_domain=amazon.com&asin=B000APVZ7W
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="author_page" \
-d amazon_domain="amazon.com" \ 
-d asin="B000APVZ7W"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "author_page",
  amazon_domain: "amazon.com",
  asin: "B000APVZ7W"
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
  'type': 'author_page',
  'amazon_domain': 'amazon.com',
  'asin': 'B000APVZ7W'
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
  'type' => 'author_page',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B000APVZ7W'
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

Copy### Author Page Parameters

The following parameters are available for all requests made when `type=author_page`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve author page data for the author specified in the asin parameter. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon author ASIN to retrieve author page data for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| url | optional | The Amazon author page URL to retrieve data from.Note: If the url parameter is supplied then the amazon\_domain and asin parameters are ignored. |
| sort\_by | optional | Determines the sort order of author titles array that is returned. Valid values are:popularitySort the author titles array by most popular first.price\_low\_to\_highSort the author titles array by lowest price first.price\_high\_to\_lowSort the author titles array by highest price first.average\_reviewSort the author titles array by highest average review first.publication\_dateSort the author titles array by most recent publication date first.most\_reviewsSort the author titles array by those with the most reviews first. |
| format\_id | optional | A format ID to determine the format of author titles returned in the titles array. Format ID's are returned in the format\_ids array in each type=author\_page results (this is necessary are the format\_id value is dynamic and can change over time). |
| page | optional | The current page of author page titles to retrieve. This pagination affects the titles array (which contains all the titles/books by the given author). Inspect the pagination.total\_pages property in the author page results to see how many pages of author titles are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Author Page Results](/docs/product-data-api/results/author-page)
