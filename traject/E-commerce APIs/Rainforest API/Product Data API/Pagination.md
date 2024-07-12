Pagination
----------

Requesting paginated results across multiple pages is one of the most common use-cases in Rainforest API.

For certain types of requests Rainforest API allows you to return data across multiple pages automatically.

You can request a single page per-request, or have Rainforest API automatically retrieve data from multiple pages and concatenate the results into one response.

  
:::hint



**API Credits and `max_page`**  
Each successfully retrieved page incurs an API credit.  
  
If the request yields fewer pages than specified, only credits for the actual number of returned pages are charged. For example, for a request with `max_page=5` that only yields 3 pages (because only 3 pages are available), then only 3 API credits are charged.  
:::

### Single Pages

To request a single page of results you should use the `page` parameter. For example, making a request with `page=5` will return data from page 5.

To find the total number of pages, and determine whether a next page is available, inspect the `pagination` object in the result JSON.

  
:::hint



**Infinate Scrolling Pagination**  
Request types that implement infinate-scrolling pagination use a `next_page_token` parameter to request the next page of results. In these cases starting pagination from an explicit page number is not possible.  
:::

### Multiple Pages

Rainforest API provides the `max_page` parameter to retrieve mutliple pages of results and concatenate them into one response - automating workloads such as "get the first 5 pages of results, if they exist".

When running a request with `max_page` set, the main array property of the response contains a concatenation of the array values from all requested pages.

#### Setting a Max Page

When using `max_page` Rainforest API will retrieve the number of pages (if available) specified in the `max_page` parameter. Results from subsequent pages will be concatenated into the main array property of the response. For example, the following request would yield data from pages 1, 2, 3, 4 and 5:

`max_page=**5**`The main array property of a request made with `max_page` will have the following properties added, making it easy to determine which physical page the current result came from:

| Property | Type | Description |
| position | number | The position of the current result on the its page. |
| page | number | The page the current result is taken from. |
| position\_overall | number | The position of the current result within all requested pages set in the max\_page parameter.Example Assuming 10 results per page and a request made with max\_page=2 the first result on page would be position\_overall=1 and the last result on page 2 would be position\_overall=20 |
#### Setting the Start Page

Set the page to start the multiple-page concatenation from by using the `page` and `max_page` parameters together. For example, the following request would yield data from pages 2, 3 & 4:

`page=**2**&max_page=**4**`#### Limits when using `max_page`

Set the page to start the multiple-page concatenation from by using the `page` and `max_page` parameters together. For example, the following request would yield data from pages 2, 3 & 4:

| Real-Time Requests | 5You can set a maximum max\_page value of 5 when making real-time requests.Note on output=htmlWhen using max\_page in combination with output=html the resultant HTML returned will consist of each page of HTML, delimited by a horizontal line break ( HTML tag).Note on include\_html=trueWhen using max\_page in combination with include\_html=true the html field is returned as an array containing the HTML of each returned page. |
| Requests in Collections | 100You can set a maximum max\_page value of 100 when adding requests to Requests.Collection limits when using max\_pageUsing max\_page on requests added to a Collection limits the total number of requests that can be added. See Collection Limits for more information. |
