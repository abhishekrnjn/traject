Question Answers Parameters
---------------------------

GET`/request`The Question Answers Parameters are applicable when making a request with `type=question_answers` to retrieve all answers for a single question on Amazon - the question is specified using either the `question_id` and `amazon_domain` parameters or the `url` parameter (where the `url` parameter contains a link to a question answers page). The parameters should be appended as querystring parameters to the Product Data API`GET`HTTP request.

Question Answers are retrieved from the [customer question answers page](https://www.amazon.com/ask/questions/Tx2YPKCGKAORFA4/1) for a single question on Amazon.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/question_answers.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Question Answers Page  
:::hint



**Question IDs**  
Rainforest API returns `question_id`'s from `type=questions` requests in the `id` parameter. See the [questions parameters](/docs/product-data-api/parameters/questions) for further information.  
:::

For example, to request all answers on `page=1` for a question with Question ID `Tx2YPKCGKAORFA4` on `amazon.com` the request would be:



HTTP



image/svg+xml
































CurlNode.JSPythonPHP  
:::::codeblocktabs


```
https://api.rainforestapi.com/request?api_key=demo&type=question_answers&amazon_domain=amazon.com&question_id=Tx2YPKCGKAORFA4
```

```
curl -L --get https://api.rainforestapi.com/request \
-d api_key="demo" \
-d type="question_answers" \
-d amazon_domain="amazon.com" \ 
-d question_id="Tx2YPKCGKAORFA4"
```

```
const axios = require('axios');

// set up the request parameters
const params = {
  api_key: "demo",
  type: "question_answers",
  amazon_domain: "amazon.com",
  question_id: "Tx2YPKCGKAORFA4"
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
  'type': 'question_answers',
  'amazon_domain': 'amazon.com',
  'question_id': 'Tx2YPKCGKAORFA4'
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
  'type' => 'question_answers',
  'amazon_domain' => 'amazon.com',
  'question_id' => 'Tx2YPKCGKAORFA4'
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

Copy### Question Answers Parameters

The following parameters are available for all requests made when `type=question_answers`.

| Parameter | Required | Description |
| --- | --- | --- |
| amazon\_domain | optional | The Amazon domain to retrieve answers for the question specified in the question\_id parameter from. For a full list of supported Amazon domains see Supported Amazon Domains.Note: If the amazon\_domain and question\_id parameters are supplied then the url parameter is ignored. |
| question\_id | optional | The ID of the question to retrieve answers for.Rainforest API returns question\_id's from type=questions requests in the id parameter. See the questions parameters for further information. |
| url | optional | The Amazon product-page URL to retrieve Question Answers from.Note: If the url parameter is supplied then the amazon\_domain and question\_id parameters are ignored. |
| page | optional | The current page of answers to retrieve. Inspect the pagination.total\_pages property in the Question Answers results to see how many pages of answers are available. |
| max\_page | optional | Use the max\_page parameter to get multiple pages of results in one request. The API will automatically paginate through pages and concatenate the results into one response.See the Pagination docs for more information. |
Next Steps

* [Question Answers Results](/docs/product-data-api/results/question-answers)
