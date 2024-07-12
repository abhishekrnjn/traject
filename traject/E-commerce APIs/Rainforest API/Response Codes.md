Response Codes
--------------

VALUE SERP will return the following HTTP Response Codes from API requests. You should inspect the response code that VALUE SERP returns to determine whether your request has been successful or not.

| HTTP Response Code | Description |
| --- | --- |
| 200 Success | Request processed successfully. |
| 402 Payment Required | Your VALUE SERP account has either run out of available credits (try enabling Overage or upgrading your Plan), or there is a payment problem. |
| 429 Too Many Requests | If you are on a Plan with a rate limit, or making a call on an endpoint that is rate-limited, and this limit is hit then an HTTP 429 response is returned. |
| 401 Unauthorized | The API Key supplied with your request is not valid. |
| 400 Bad Request | The request you specified is invalid. The details of the error are shown in the JSON body of the response. The most common cause of an HTTP 400 response is passing invalid parameters to the APIs, or combinations of parameter values that are not supported. |
| 404 Not Found | The request URL you specified is invalid. Check the request URL you are using (if you receive an HTTP 404 it's likely the path you're using is not correct). It could also be you are using an incorrect HTTP verb - i.e. making an HTTP POST where a GET is required. |
| 500 Internal Server Error | There was a problem processing your request. You should retry your request after a delay and if you continue to experience the same result please contact our support team. |
| 503 Service Unavailable | Returned in response to the skip\_on\_incident request parameter being set and there being a live parsing incident ongoing at the time of the request. The body of the response will contain a JSON object whos message property defines the type of parsing incident that is currently active. |
