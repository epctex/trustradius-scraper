# Actor - Trustradius Scraper

## Trustradius scraper

Since Trustradius doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Trustradius data scraper supports the following features:

-   Search any vendor - You can search for any vendor and its detailed information  according to your needs.

-   Scrape products - Scrape any products with their reviews in a very detailed and structured from Trustradius.

-   Scrape reviews - Fetch any reviews that has been published on Trustradius.

-   Scrape users - Scrape any users and retrieve their information.

-   Scrape and search - Within the integrated search functionality, you can search for anything right away from the Trustradius.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/trustradius-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Trustradius that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search               | String  | (optional) Keyword that you want to search on Trustradius.                                                                                                                                                       |
| mode               | String  | (optional) Mode that is required when you provide a search keyword. Can be `all`, `product` or `vendor`.                                                                                                                                                       |
| startUrls            | Array   | (optional) List of Trustradius URLs. You should only provide user, product, vendor or search URLs                                                                                                                 |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.                                                          |
| maxItems             | Integer | (optional) You can limit scraped items. This should be useful when you search through the big subcategories.                                                                                                |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data                                                                                                                    |
| customMapFunction | String  | (optional) Function that takes each objects handle as argument and returns object with executing the function                                                                                                                     |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific item URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as items as possible. Therefore, it forefronts all item detail requests. If actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.06 compute units.

### Trustradius Scraper Input example

```json
{
  "startUrls":[
    "https://www.trustradius.com/users/5c24577c4452bb002b85451a",
    "https://www.trustradius.com/search?t=product&q=food",
    "https://www.trustradius.com/search?t=vendor&t=product&q=food",
    "https://www.trustradius.com/products?q=food",
    "https://www.trustradius.com/vendors?q=food"
  ],
  "includeReviews":true,
  "proxy":{
    "useApifyProxy": true
  },
  "search":"pro",
  "mode":"all",
  "maxItems": 5000,
  "endPage": 2
}


```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Trustradius Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Trustradius actor.

## Scraped Trustradius Output

The structure of each item in Trustradius looks like this:

### User Detail

```json
{
  "url": "https://www.trustradius.com/users/5c24577c4452bb002b85451a",
  "name": "",
  "image": "https://media.trustradius.com/profile-photos/5c24577c4452bb002b85451a/841ZA7UO3CHD.jpeg",
  "score": 5,
  "Title": "Dietitian Consultant🌮 | Marketing Expert | Business Development✨ Freelancer/Contractor/Consultant",
  "Job Type": "Consultant",
  "Department": "Marketing",
  "Company": "Self Employed",
  "Industry": "Marketing & Advertising",
  "Size": "1-10 employees",
  "skills": [
    {
      "product": "Canva",
      "experience": "7 years",
      "expertise": ""
    },
    {
      "product": "Pipedrive",
      "experience": "7 years",
      "expertise": ""
    },
    {
      "product": "HubSpot Academy",
      "experience": "7 years",
      "expertise": ""
    },
    {
      "product": "Hootsuite",
      "experience": "7 years",
      "expertise": ""
    }
  ],
  "badges": [
    "Pundit- Org Chart",
    "Pundit- Presentation",
    "Pundit- Graphics"
  ]
}
```

### Product Detail

```json
{
	"id": "5061d969e1ff5d020000006c",
	"slug": "dropbox",
	"scrapedType": "product",
	"url": "https://www.trustradius.com/products/dropbox",
	"name": "Dropbox",
	"image": "https://dudodiprj2sv7.cloudfront.net/product-logos/SG/31/5CMU1A9BSNHP.png",
	"rating": 7.58,
	"alternatives": [
		{
			"id": "5eb08e7e649978003e5ef1e7",
			"name": "Nextcloud",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "560d603d3428681500ac3b37",
			"name": "Amazon Drive",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "55913c5d282ced2c00583018",
			"name": "Veeam Backup & Replication",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "5b43b68e616fa800126219fb",
			"name": "WeTransfer",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "583f6190aff37e000f13dba2",
			"name": "Microsoft 365",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "5c818a237b6b57001a0f0256",
			"name": "Microsoft Teams",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "55c11e38a0f02c2c00b21537",
			"name": "MEGA",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "560d5e9c70c1521a00f8ff1e",
			"name": "IDrive",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "55e5f49b4810c2250009f133",
			"name": "Amazon S3 (Simple Storage Service)",
			"url": "https://www.trustradius.com/products/undefined"
		},
		{
			"id": "55eef1e346ad210f00e0f40d",
			"name": "MediaFire",
			"url": "https://www.trustradius.com/products/undefined"
		}
	],
	"details": "Dropbox is a service for file syncing and sharing, or for cloud storage.",
	"categories": [
		"File Sharing",
		"File Sync",
		"Cloud Storage"
	],
	"homepage": "",
	"operatingSystems": [],
	"deploymentTypes": [
		"saas"
	],
	"mobileOperatingSystems": [],
	"countries": [],
	"languages": [],
	"features": [],
	"awards": [
		"Top Rated 2022",
		"Top Rated 2019",
		"Top Rated 2020",
		"Top Rated 2021",
		"Best Of Relationship 2022",
		"Best Of Value 2022",
		"Best Of Feature Set 2022"
	],
	"editionPricing": [
		{
			"deploymentTypes": [
				"saas"
			],
			"_id": "5ff4c431bc6ed0002a6169b4",
			"name": "Plus",
			"price": "$11.99",
			"durationTerms": "per month"
		},
		{
			"deploymentTypes": [
				"saas"
			],
			"_id": "5ff4c43a74ed7b001edfbd4a",
			"name": "Family",
			"price": "$19.99",
			"durationTerms": "per month"
		},
		{
			"deploymentTypes": [
				"saas"
			],
			"_id": "5ff4c42614c49c00410f991c",
			"name": "Basic",
			"price": "Free"
		}
	],
	"entryLevelFee": {
		"fee": "",
		"otherTerms": "",
		"durationTerms": null,
		"otherDurationTerms": "",
		"otherUnitTerms": "",
		"unitTerms": null
	},
	"startingPrice": {
		"durationTerms": "per month",
		"price": null,
		"otherDurationTerms": "",
		"otherUnitTerms": "",
		"unitTerms": null
	},
	"ratingsNumber": 1974
}
```
### Vendor Detail

```json
{
  "url": "https://www.trustradius.com/vendors/pro-unlimited",
  "name": "PRO Unlimited",
  "image": "https://media.trustradius.com/vendor-logos/vb/dy/OT96TNPGWP7L-180x180.JPEG",
  "description": "",
  "socialLinks": [
    "http://prounlimited.com",
    "https://twitter.com/prounlimited"
  ],
  "products": [
    {
      "name": "PRO Unlimited Wand VMS",
      "url": "https://www.trustradius.com/products/pro-unlimited-wand-vms/reviews",
      "rating": 3.5
    }
  ]
}
```
