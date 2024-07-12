Questions Parameters
--------------------

GET`/request`The Questions Parameters are applicable when making a request with `type=questions` to retrieve customer Questions & Answers for a single product on Amazon - the product is specified using either the `asin` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to an Amazon product page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Questions are retrieved from the [customer questions page](https://www.amazon.com/ask/questions/asin/B073JYC4XM/1/) for a single product on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/questions.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Questions & Answers Page  
:::hint



**Retrieving all answers for a question**  
A `type=questions` request retrieves 10 questions per request along with the top answer for each question. To retrieve **all** answers for a question you should pass the `question_id` into a `type=question_answers` request. See the [question answers parameters](/docs/product-data-api/parameters/question-answers) for more information.  
:::

For example, to request all `page=1` of customer Questions, sorted by `most_helpful`, for the ASIN `B073JYC4XM` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=questions&page=1&amazon_domain=amazon.com&asin=B073JYC4XM&sort_by=most_helpful
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="questions" \
-d page="1" \
-d amazon_domain="amazon.com" \ 
-d asin="B073JYC4XM" \
-d sort_by="most_helpful"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "questions",
  page: "1",
  amazon_domain: "amazon.com",
  asin: "B073JYC4XM",
  sort_by: "most_helpful"
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
  'type': 'questions',
  'page': '1',
  'amazon_domain': 'amazon.com',
  'asin': 'B073JYC4XM',
  'sort_by': 'most_helpful'
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
  'type' => 'questions',
  'page' => '1',
  'amazon_domain' => 'amazon.com',
  'asin' => 'B073JYC4XM',
  'sort_by' => 'most_helpful'
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

Copy### Questions Parameters

The following parameters are available for all requests made when `type=questions`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve Questions & Answers for the product specified in the asin parameter from. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and asin parameters are supplied then the url parameter is ignored. |
| asin | optional | The Amazon ASIN (product ID) to retrieve Questions & Answers for. Used in combination with the amazon\_domain parameter.Note: If the asin and amazon\_domain parameters are supplied then the url parameter is ignored. |
| url | optional | The Amazon product-page URL to retrieve Questions & Answers from.Note: If the url parameter is supplied then the amazon\_domain and asin parameters are ignored. |
| sort\_by | optional | Determines the sort order of Questions & Answers to return. Valid values are:most\_helpfulReturns Questions & Answers with the most helpful first.most\_recentReturns Questions & Answers in date order, with the most recent first. |
| page | optional | The current page of Questions & Answers to retrieve. Inspect the pagination.total\_pages property in the Questions results to see how many pages of questions are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Questions Results](/docs/product-data-api/results/questions)
* [Question Answers Parameters](/docs/product-data-api/parameters/question-answers)
* [Question Answers Results](/docs/product-data-api/results/question-answers)
