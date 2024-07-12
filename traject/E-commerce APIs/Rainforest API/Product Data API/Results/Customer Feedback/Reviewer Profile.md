Reviewer Profile Results
------------------------

When making a request with the `type` [parameter](/docs/product-data-api/parameters/reviewer-profile) set to `type=reviewer_profile` Rainforest API will return details of reviewer specified in either the `reviewer_id` and `amazon_domain` parameters or the `url` parameter.

Reviewer profile details are retrieved from the [reviewer profile page](https://www.amazon.com/gp/profile/amzn1.account.AHBEI6Q4F4WHRIFK5CWQMRVPOQMA). You can retrieve the `reviewer_id` value for a given reviewer from other Rainforest requests, such as `type=reviews` requests.

![](https://apiimages.imgix.net/rainforestapi/images/png/docs/reviewer_profile.png?auto=format&ixlib=react-9.5.1-beta.1&w=600)Reviewer Profile PageAn example of the JSON object returned from an Reviewer Profile request is shown below:

{"request\_info":{...}"request\_metadata":{...}"request\_parameters":{...}"reviewer\_details":{...}"reviews":[...]}CopyRainforest API returns the following properties for Reviewer Profile requests:

| Property | Type | Description |
| reviewer\_details | object | | Reviewer Details Object | The reviewer details object contains address, contact and ratings details about the seller. |
| --- | --- |
namestringThe name of the reviewer.descriptionstringThe description of the reviewer.locationstringThe location of the reviewer.badgesarrayAn array of strings representing the "badges" the reviewer has acquired, i.e. "TOP 50 REVIEWER", "VINE VOICE" etc.occupationstringThe occupation of the reviewer.ranknumberThe current rank of the reviewer amoungst all reviewers.helpful\_votesnumberThe total number of helpful votes the reviewer has received for their reviews.hearts\_countnumberThe total number of hearts ideas from this reviewer have received.idea\_lists\_countnumberThe number of idea lists this reviewer has published.reviews\_countnumberThe total number of reviews this reviewer has written.socialobjectAn object containing the following properties containing links to the reviewers public social profiles: facebook, twitter, pinterest, youtube and instagram |
| reviews | array | | Reviews Array | The reviews array contains the first page of customer reviews shown on the reviewer profile page. The review object has the following properties: |
| --- | --- |
idstringThe ID of the review.helpful\_votesnumberThe number of helpful votes this review has received.titlestringThe title of the review.bodystringThe body text of the review.linkstringA link to the review.ratingnumberThe rating given to the product by the reviewer, out of 5.ratingnumberThe rating given to the product by the reviewer, out of 5.dateobject| Date Object | The date object contains details about the date of the review. |
| --- | --- |
utcstringThe date of the review reply in ISO 8601 format.verified\_purchasebooleanTrue/false whether the reviewer is a verified purchaser of the product being reviewed.amazon\_vinebooleanTrue/false whether the review is part of the Amazon Vine program, or not.languagestringThe language of the review - i.e. en\_US.productobject| Product Object | The product object contains details of the product being reviewed. |
| --- | --- |
asinstringThe ASIN of the product.titlestringThe title of the product.ratingstringThe average rating the product has received, across all ratings of the product.ratings\_totalstringThe total number of ratings this product has received.is\_primebooleanTrue/false whether this product is Prime-eligable, or not.linkstringA link to the product page.imagestringA link to the main image of the product. |
Next Steps

* [Reviewer Profile Parameters](/docs/product-data-api/parameters/reviewer-profile)
