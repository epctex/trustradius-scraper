[https://apify.com/epctex/trustradius-scraper](https://apify.com/epctex/trustradius-scraper?fpr=yhdrb)

# Actor - Trustradius Scraper

## Trustradius scraper

Since Trustradius doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Trustradius data scraper supports the following features:

-   Search any vendor - You can search for any vendor and its detailed information according to your needs.

-   Scrape products - Scrape any products with their reviews in a very detailed and structured from Trustradius.

-   Scrape reviews - Fetch any reviews that have been published on Trustradius.

-   Scrape users - Scrape any users and retrieve their information.

-   Scrape and search - Within the integrated search functionality, you can search for anything right away from Trustradius.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/trustradius-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Trustradius that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Trustradius.

- `mode`: (Optional) (String) Mode that is required when you provide a search keyword. Can be `all`, `product`, or `vendor`.

- `includeReviews`: (Optional) (Boolean) Adding reviews into the product objects is optional and by default, it is `false`. If you want to scrape the reviews of the companies, then you can set this option as `true`.

- `startUrls`: (Optional) (Array) List of Trustradius URLs. You should only provide user, product, vendor, or search URLs.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. The default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific item URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape many items as possible. Therefore, it forefronts all item detail requests. If the actor doesn't block very often it'll scrape 100 items in 1 minute with ~0.04-0.06 compute units.

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

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Trustradius Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Trustradius actor.

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
    "ratingsNumber": 1974,
    "reviews": [
        {
            "userName": "User Name",
            "date": "2022-03-29T23:45:59.315Z",
            "editedDate": "2022-03-29T13:44:09.330Z",
            "submittedDate": "2022-03-29T14:06:11.733Z",
            "lastUpdatedDate": "2022-03-29T23:45:59.315Z",
            "title": "Filestage 2022-03-29 08:14:22",
            "userOccupation": "Professional",
            "userCompany": "Company Name",
            "rating": 10,
            "questions": [
                {
                    "title": "Use Cases and Deployment Scope",
                    "answer": "We use Dropbox to organize, proof, and get approvals for any type of collateral we are producing. It allows us to create pieces from concept to final press-ready mechanicals. Everyone knows at all times where the project is in the process and knows when it is time for them to move forward with their contribution. Everything is documented, so there is never confusion about how we got to the final piece."
                },
                {
                    "title": "Pros",
                    "answer": "Compares past and present versions.\nMakes commenting easy.\nEasy navigation."
                },
                {
                    "title": "Cons",
                    "answer": "Alerts can be improved.\nWould love to have this be an application on my desktop so I don't have to go through my browser every time."
                },
                {
                    "title": "Likelihood to Recommend",
                    "answer": "I think Dropbox is perfect for projects where there is a team involved and several eyes need to be on the project.  I don't think it is necessary for small projects where the approval process only goes through one other person. It also keeps everyone on schedule without being annoying."
                },
                {
                    "title": "Return on Investment",
                    "answer": "In general, it has saved the company time (which is money) by keeping us organized and having everyone on the same page continuously."
                },
                {
                    "title": "Alternatives Considered",
                    "answer": "We use Slack  - but not really for organizing, proofing, or approving projects. We use it more as a communication tool for the employees that are spread across the country. We will occasionally post smaller jobs there - but most of our projects go through Dropbox."
                },
                {
                    "title": "Other Software Used",
                    "answer": "Adobe Illustrator CC, Adobe InDesign, Adobe Acrobat Reader DC"
                }
            ]
        },
    ]
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

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
