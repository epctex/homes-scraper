# Actor - Homes.com Scraper

## Homes.com scraper

Since Homes.com doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Homes.com data scraper supports the following features:

-   Search anything, use any filter - Getting any search result is at your fingertips. Use any filter, focus on any location and immediately retrieve properties which are for sale, for rent or already sold.

-   Get listings of agents - Are you looking for listings of an agent? No worries. Use agent's profile URL and get everything with ease.

-   Retrieve any property - Price, beds, baths, amenities, tax history and many other detailed information are available at your consumption. Rental, for sale or sold properties are available!

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/homes-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Homes.com that should be visited. Possible fields are:

- `startUrls`: (Required) (Array) List of Homes.com URLs. You should only provide search, list, agent or property detail URLs.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 3 minutes with ~0.07-0.10 compute units.

### Homes.com Scraper Input example

```json
{
  "startUrls":[
    "https://www.homes.com/property/4414-s-frontenac-st-seattle-wa/89p4n9gbb0k64/",
    "https://www.homes.com/real-estate-agents/devin-haub/5yk0pjp/",
    "https://www.homes.com/los-angeles-ca/",
    "https://www.homes.com/los-angeles-ca/homes-for-rent/",
    "https://www.homes.com/los-angeles-ca/sold/"
  ],
  "endPage":3,
  "maxItems": 10,
  "proxy":{
    "useApifyProxy":true
  }
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Homes.com Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Homes.com actor.

## Scraped Homes.com Properties

The structure of each property in Homes.com looks like this:

### Property Detail

```json
{
	"id": "89p4n9gbb0k64",
	"url": "https://www.homes.com/property/4414-s-frontenac-st-seattle-wa/89p4n9gbb0k64/",
	"propertyType": "FORSALE",
	"name": "4414 S Frontenac St, Seattle, WA 98118 - For Sale",
	"isMultifamily": false,
	"agentFullName": "John Cowan",
	"agentPhone": "(206) 422-8741",
	"agentPhoto": "https://imagescdn.homes.com/i2/iP0WwRFttvr2NJp3_GbktPWoeBD-ZVgO4OhrUiHWp3k/115/image.jpg?p=1",
	"agentEmail": "jcowan@windermere.com",
	"agentLicenseNumber": "License #96273",
	"agencyName": "Windermere Real Estate Co.",
	"coordinate": {
		"lt": 47.54003,
		"ln": -122.27729
	},
	"city": "Seattle",
	"propertyAddress": "4414 S Frontenac St",
	"state": "WA",
	"recentPropertyTax": 5519,
	"listingType": "Resale",
	"propertyFullAddress": "4414 S Frontenac St",
	"minBeds": 3,
	"maxBeds": 3,
	"minBaths": 2,
	"price": 600000,
	"postalCode": "98118",
	"interestRates": [
		{
			"year": 30,
			"rate": 0.0694
		},
		{
			"year": 15,
			"rate": 0.0623
		}
	],
	"beds": 3,
	"baths": 2,
	"currentListPrice": 600000,
	"listDate": "04/15/2023",
	"mlsKey": "zc4n71z",
	"mlsSource": "Northwest Multiple Listing Service",
	"mlsNumber": "MLS#: NWM2056269",
	"mlsApn": "APN: 381240-0804",
	"yearBuilt": 1960,
	"images": [
		{
			"type": "PrimaryPhoto",
			"url": "https://images.homes.com/listings/114/8969915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/2079915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/7079915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/0179915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/3179915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/7179915813-615817351-original.jpg"
		},
		{
			"type": "BuildingPhoto",
			"url": "https://images.homes.com/listings/117/9300025813-615817351-original.jpg"
		}
	],
	"neighborhood": "Kelseys Brighton Beach Acre Trails",
	"sqft": 910,
	"lotsize": 6098,
	"description": "Builder alert! Level lot with alleyway access offers development potential in vibrant Brighton/Othello neighborhood. Possible option for SFR/AADU build or 6-home cottage site. Plans for 6-home site ready to transfer to buyer. Just two blocks to Othello Link Light Rail Station and Othello Park. Restaurants, grocery & coffee shops nearby. Minutes to Seward Park and Lake Washington. Exceptionally simple access around the Puget Sound with proximity to transit, plus access to 1-5 and I-90. Home sold as-is - value is in the land.",
	"schools": [
		{
			"name": "",
			"type": "Public",
			"distance": "4 min walk",
			"rating": "3/ 10"
		},
		{
			"name": "",
			"type": "Public",
			"distance": "14 min walk",
			"rating": "5/ 10"
		},
		{
			"name": "",
			"type": "Public",
			"distance": "8 min drive",
			"rating": "4/ 10"
		},
		{
			"name": "",
			"type": "Charter",
			"distance": "9 min walk",
			"rating": "5/ 10"
		}
	],
	"parks": [
		{
			"name": "Pritchard Island Beach",
			"distance": "3 min drive"
		},
		{
			"name": "Kubota Gardens",
			"distance": "5 min drive"
		},
		{
			"name": "Genesee Park and Playfield",
			"distance": "6 min drive"
		},
		{
			"name": "Seward Park Environmental & Audubon Center",
			"distance": "8 min drive"
		}
	],
	"transportation": [
		{
			"type": "Subway",
			"name": "ST Light Rail & Othello Station (NB)",
			"distance": "7 min walk"
		},
		{
			"type": "Subway",
			"name": "Othello",
			"distance": "7 min walk"
		},
		{
			"type": "Commuter Rail",
			"name": "King Street (Seattle) Station",
			"distance": "13 min drive"
		},
		{
			"type": "Commuter Rail",
			"name": "Tukwila Station",
			"distance": "14 min drive"
		},
		{
			"type": "Airport",
			"name": "Seattle-Tacoma International",
			"distance": "29 min drive"
		},
		{
			"type": "Airport",
			"name": "Kenmore Air Harbor Inc",
			"distance": "35 min drive"
		}
	],
	"scores": [
		{
			"type": "Walk Score®",
			"tagline": "Very Walkable"
		},
		{
			"type": "Transit Score®",
			"tagline": "Good Transit"
		},
		{
			"type": "Sound Score®",
			"tagline": "Active"
		},
		{
			"type": "Bike Score®",
			"tagline": "Very Bikeable"
		}
	],
	"amenities": [
		{
			"name": "Property Type",
			"value": "Residential"
		},
		{
			"name": "Year Built",
			"value": "1960"
		},
		{
			"name": "Property Sub Type",
			"value": "Residential"
		},
		{
			"name": "Lot Size Acres",
			"value": "0.1458"
		},
		{
			"name": "Co List Office Mls Id",
			"value": "NWM7918"
		},
		{
			"name": "Co List Office Phone",
			"value": "206-522-9600"
		},
		{
			"name": "Cumulative Days on Market",
			"value": "25"
		},
		{
			"name": "Subdivision Name",
			"value": "Brighton"
		},
		{
			"name": "Building Name",
			"value": "Kelseys Brighton Beach Acre Trs"
		},
		{
			"name": "Carport Y N",
			"value": "No"
		},
		{
			"name": "Garage Yn",
			"value": "Yes"
		},
		{
			"name": "New Construction",
			"value": "No"
		},
		{
			"name": "Structure Type",
			"value": "House"
		},
		{
			"name": "Power Production Type",
			"value": "Electric"
		},
		{
			"name": "Basement",
			"value": "None"
		},
		{
			"name": "Full Bathrooms",
			"value": "1"
		},
		{
			"name": "Half Bathrooms",
			"value": "1"
		},
		{
			"name": "Possible Bedrooms",
			"value": "3"
		},
		{
			"name": "Total Bedrooms",
			"value": "3"
		},
		{
			"name": "Entry Location",
			"value": "Main"
		},
		{
			"name": "Fireplace",
			"value": "No"
		},
		{
			"name": "Interior Amenities",
			"value": "Dining Room"
		},
		{
			"name": "Main Level Bedrooms",
			"value": "3"
		},
		{
			"name": "Bathrooms",
			"value": "1.5"
		},
		{
			"name": "Roof",
			"value": "Composition"
		},
		{
			"name": "Lot Features",
			"value": "Alley, Curbs, Paved, Sidewalk"
		},
		{
			"name": "Waterfront",
			"value": "No"
		},
		{
			"name": "Exterior Features",
			"value": "Wood Products"
		},
		{
			"name": "Attached Garage",
			"value": "No"
		},
		{
			"name": "Open Parking",
			"value": "No"
		},
		{
			"name": "Parking Features",
			"value": "Driveway, Detached Garage"
		},
		{
			"name": "Sewer",
			"value": "Sewer Connected"
		},
		{
			"name": "Water Source",
			"value": "Public"
		},
		{
			"name": "Cooling",
			"value": "None"
		},
		{
			"name": "Cooling Y N",
			"value": "No"
		},
		{
			"name": "Heating",
			"value": "Wall Unit(s)"
		},
		{
			"name": "Heating Yn",
			"value": "Yes"
		},
		{
			"name": "Senior Community",
			"value": "No"
		},
		{
			"name": "Association",
			"value": "No"
		},
		{
			"name": "Parcel Number",
			"value": "3812400804"
		},
		{
			"name": "Topography",
			"value": "Level,PartialSlope"
		},
		{
			"name": "Land Lease",
			"value": "No"
		},
		{
			"name": "Lot Size Sq Ft",
			"value": "6350"
		},
		{
			"name": "Irrigation Water Rights",
			"value": "No"
		},
		{
			"name": "Furnished",
			"value": "Unfurnished"
		},
		{
			"name": "Year",
			"value": "2022"
		},
		{
			"name": "Tax Annual Amount",
			"value": "5197"
		}
	]
}
```
