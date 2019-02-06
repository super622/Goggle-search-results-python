# Google Search Results in Python

This Python package allows you to scrape and parse Google Search Results using [SerpWow](https://serpwow.com). In addition to [Search](https://serpwow.com/docs/search/overview) you can also use this package to access the SerpWow [Locations API](https://serpwow.com/docs/locations/overview) and [Account API](https://serpwow.com/docs/account/overview).

## Installation
You can install google-search-results-serpwow with:

```shell
$ pip install google-search-results-serpwow
```

and upgrade with:

```shell
$ pip install google-search-results-serpwow --upgrade
```

## Documentation
We have included examples here but full SerpWow API documentation is available at the [API Docs](https://serpwow.com/docs):
- [Search API Docs](https://serpwow.com/docs/search/overview) 
- [Locations API Docs](https://serpwow.com/docs/locations/overview) 
- [Account API Docs](https://serpwow.com/docs/account/overview)

You can also use the [API Playground](https://app.serpwow.com/playground) to visually build Google search requests using SerpWow.

## Simple Example
Simplest example for a standard query "pizza", returning the Google SERP (Search Engine Results Page) data as JSON:
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# set up a dict for the search parameters
params = {
  "q" : "pizza"
}

# retrieve the search results as JSON
result = serpwow.get_json(params)

# pretty-print the result
print json.dumps(result, indent=2, sort_keys=True)
```

## Response
Except (shortened for brevity) of the JSON response returned is shown below. For details of all of the fields from the Google search results page that are parsed please see the [docs](https://serpwow.com/docs/search/results/overview).
```json
{
  request_info: {
    success: true
  },
  search_metadata: {
    id: "20c8e44e9cacedabbdff2d9b7e854436056d4f33",
    google_url: "https://www.google.com/search?q=pizza&oq=pizza&sourceid=chrome&ie=UTF-8",
    total_time_taken: 0.14
  },
  search_parameters: {
    q: "pizza"
  },
  search_information: {
    total_results: 1480000000,
    time_taken_displayed: 0.45,
    query_displayed: "pizza",
    detected_location: "Ireland"
  },
  local_map: {
    link: "https://www.google.com/search?q=pizza&npsic=0&rflfq=1&rldoc=1&rlha=0&rllag=53350059,-6249133,1754&tbm=lcl&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4QtgN6BAgBEAQ",
    gps_coordinates: {
      latitude: 53.350059,
      longitude: -6.249133,
      altitude: 1754
    },
    local_results: [{
        position: 1,
        title: "Apache Pizza Temple Bar",
        extensions: [
          "American-style pizza-delivery chain"
        ],
        rating: 3.6,
        reviews: 382,
        type: "Pizza",
        block_position: 1
      },
      {
        position: 2,
        title: "Ciao Woodfire Pizza",
        extensions: [
          "Casual",
          "Vegetarian options",
          "Delivery"
        ],
        rating: 4.3,
        reviews: 80,
        price: "€",
        type: "Pizza",
        block_position: 1
      },
      {
        position: 3,
        title: "Independent Pizza Company",
        extensions: [
          "American-style pizza restaurant"
        ],
        rating: 4.4,
        reviews: 458,
        type: "Pizza",
        block_position: 1
      }
    ],
    knowledge_graph: {
      title: "Pizza",
      type: "Dish",
      description: "Pizza is a savory dish of Italian origin, consisting of a usually round, flattened base of leavened wheat-based dough topped with tomatoes, cheese, and various other ingredients baked at a high temperature, traditionally in a wood-fired oven.",
      source: {
        name: "Wikipedia",
        link: "https://en.wikipedia.org/wiki/Pizza"
      },
      nutrition_facts: {
        total_fat: [
          "10 g",
          "15%"
        ],
        sugar: [
          "3.6 g"
        ],
        protein: [
          "11 g",
          "22%"
        ]
      }
    },
    related_searches: [{
        query: "apache pizza",
        link: "https://www.google.com/search?q=apache+pizza&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4Q1QIoAHoECAUQAQ"
      },
      {
        query: "domino's pizza",
        link: "https://www.google.com/search?q=domino%27s+pizza&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4Q1QIoAXoECAUQAg"
      }
    ],
    organic_results: [{
        position: 1,
        title: "10 Best Pizzas in Dublin - A slice of the city for every price point ...",
        link: "https://www.independent.ie/life/travel/ireland/10-best-pizzas-in-dublin-a-slice-of-the-city-for-every-price-point-37248689.html",
        domain: "www.independent.ie",
        displayed_link: "https://www.independent.ie/.../10-best-pizzas-in-dublin-a-slice-of-the-city-for-every-p...",
        snippet: "Oct 20, 2018 - Looking for the best pizza in Dublin? Pól Ó Conghaile scours the city for top-notch pie... whatever your budget.",
        cached_page_link: "https://webcache.googleusercontent.com/search?q=cache:wezzRov42dkJ:https://www.independent.ie/life/travel/ireland/10-best-pizzas-in-dublin-a-slice-of-the-city-for-every-price-point-37248689.html+&cd=4&hl=en&ct=clnk&gl=ie",
        block_position: 2
      },
      {
        position: 2,
        title: "Domino's Pizza: Pizza for Delivery or Takeaway Near You",
        link: "https://www.dominos.ie/",
        domain: "www.dominos.ie",
        displayed_link: "https://www.dominos.ie/",
        snippet: "Visit Domino's Pizza for a tasty pizza delivery or takeaway near you. Order online today for a piping hot pizza delivered directly to your door.",
        cached_page_link: "https://webcache.googleusercontent.com/search?q=cache:djFeLNPbR3wJ:https://www.dominos.ie/+&cd=5&hl=en&ct=clnk&gl=ie",
        related_page_link: "https://www.google.com/search?q=related:https://www.dominos.ie/+pizza&tbo=1&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4QHzAEegQICRAF",
        block_position: 2
      },
      {
        position: 3,
        title: "Pizza Takeaway and Restaurant Delivery | Order Online at Just Eat",
        link: "https://www.just-eat.ie/takeaways/pizza/",
        domain: "www.just-eat.ie",
        displayed_link: "https://www.just-eat.ie › Home › All cuisine types › Pizza",
        snippet: "Who doesn't love pizza, right? Order online with Just Eat for collection or delivery from the best pizza takeaways and restaurants in your local area.",
        cached_page_link: "https://webcache.googleusercontent.com/search?q=cache:G8MduioP3LoJ:https://www.just-eat.ie/takeaways/pizza/+&cd=6&hl=en&ct=clnk&gl=ie",
        related_page_link: "https://www.google.com/search?q=related:https://www.just-eat.ie/takeaways/pizza/+pizza&tbo=1&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4QHzAFegQICxAG",
        block_position: 2
      },
      {
        position: 4,
        title: "Pizza Delivery, Deals & Takeaway | Order Online with Pizza Hut Delivery",
        link: "https://www.pizzahutdelivery.ie/",
        domain: "www.pizzahutdelivery.ie",
        displayed_link: "https://www.pizzahutdelivery.ie/",
        snippet: "Pizza Hut - Order pizza online for free delivery, get the best deals, and find your nearest branch for dine-in or collection.",
        cached_page_link: "https://webcache.googleusercontent.com/search?q=cache:2jlup2QZFpgJ:https://www.pizzahutdelivery.ie/+&cd=7&hl=en&ct=clnk&gl=ie",
        block_position: 2
      }
    ],
    related_places: [{
      link: "https://www.google.com/search?tbm=lcl&q=pizza&rflfq=1&num=20&stick=H4sIAAAAAAAAAB1QS0pDQRAki4hrn7h4qxyhu_q_9SZCAgZBxASEHMcTeC5PYT1nMTNdUNVVdX-3LuhAD6bVBpIR0usSWhs0aWLpKtG6PqoHzMJtvNOlrBvrg0HGiuxogZWUrsu0eKVqiyREuoLgtqCRQECjPapATdOSGDWM6ZBVgXWx7HaqasLUPEVqXXSg6QUTunNRWlsXzj4akUihv6LnTRTigxiZbO9IDfKtaHyykBV0xK1O0OiSwhyEt2_2yecbMtqaUdxZuakGSqs90TXFuJlGFJ1TMkwz5mAFyv6y1EE2I4g43P-9Bn9iwhSTklXKVhTmw01myRODCoLOPtiGIVTLmFF-drvf3dPz6XI9HM_v76fPy-HrfH09vJ2Pl-_9_uN8u738AZh-lQfPAQAA&sa=X&ved=2ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4Q_KoBMA16BAgCEAM",
      theme: "Best dinners with kids",
      places: "Pinocchio Italian Restaurant - Temple Bar, Cafe Topolisand more",
      images: [
        "https://lh5.googleusercontent.com/p/AF1QipNhGt40OpSS408waVJUHeItGrrGqImmEKzuVbBv=w152-h152-n-k-no"
      ]
    }],
    pagination: {
      current: "1",
      next: "https://www.google.com/search?q=pizza&ei=fRZQXMKqL8en1fAPitiT8AI&start=10&sa=N&ved=0ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4Q8NMDCOkB",
      other_pages: {
        2: "https://www.google.com/search?q=pizza&ei=fRZQXMKqL8en1fAPitiT8AI&start=10&sa=N&ved=0ahUKEwiC3cLZ0JLgAhXHUxUIHQrsBC4Q8tMDCNcB"
      },
      api_pagination: {
        next: "https://api.serpwow.com/live/search?api_key=4BCC1B8B&q=pizza&start=10",
        other_pages: {
          2: "https://api.serpwow.com/live/search?api_key=4BCC1B8B&q=pizza&start=10"
        }
      }
    },
  }
```

## Getting an API Key
To get a free API Key head over to [app.serpwow.com/signup](https://app.serpwow.com/signup).


## Searching with a location
Example of a Google query geo-locating the query as if the user were located in New York. 
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# set up a dict for the query (q) and location parameters
# note that the "location" parameter should be a value
# returned from the Locations API
params = {
  "q" : "pizza",
  "location" : "New York,New York,United States"
}

# retrieve the search results as JSON
result = serpwow.get_json(params)

# pretty-print the result
print json.dumps(result, indent=2, sort_keys=True)
```

## Searching Google Places, Google Videos, Google Images, Google Shopping and Google News
Use the ``search_type`` param to search Google Places, Videos, Images and News. See the [Search API Parameters Docs](https://serpwow.com/docs/search/parameters) for full details of the additional params available for each search type.
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# perform a search on Google News, just looking at blogs, filtering out duplicates
params = {
  "q" : "football news",
  "search_type" : "news",
  "news_type" : "blogs",
  "show_duplicates" : "false"
}
result = serpwow.get_json(params)
print json.dumps(result, indent=2, sort_keys=True)

# perform a search on Google Places for "plumber" in London
params = {
  "search_type" : "places",
  "q" : "plumber",
  "location" : "London,England,United Kingdom"
}
result = serpwow.get_json(params)
print json.dumps(result, indent=2, sort_keys=True)

# perform an image search on Google Images for "red flowers"
params = {
  "q" : "red flowers",
  "search_type" : "images"
}
result = serpwow.get_json(params)
print json.dumps(result, indent=2, sort_keys=True)
```

## Returning results as JSON, HTML and CSV
``google-search-results-serpwow`` can return data in JSON, HTML and CSV formats using the ``get_json``, ``get_html`` and ``get_csv`` methods. For CSV results use the ``csv_fields`` param ([docs](https://serpwow.com/docs/search/csvfields)) to request specific result fields.
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# set up a dict for the query (q) and location parameters
# note that the "location" parameter should be a value
# returned from the Locations API
params = {
  "q" : "pizza",
  "location" : "New York,New York,United States"
}

# retrieve the search results as JSON
result_json = serpwow.get_json(params)

# retrieve the search results as HTML
result_html = serpwow.get_html(params)

# retrieve the search results as CSV
result_csv = serpwow.get_csv(params)
```

## Requesting mobile and tablet results
To request that SerpWow renders the Google search results via a mobile or tablet browser use the ``device`` param:
```python
from serpwow.google_search_results import GoogleSearchResults
import json

serpwow = GoogleSearchResults("demo")

# set up the mobile params
params_mobile = {
  "q" : "pizza",
  "device" : "mobile"
}

# set up the tablet params
params_tablet = {
  "q" : "pizza",
  "device" : "tablet"
}

# set up the desktop params (note we omit the "device" param)
params_desktop = {
  "q" : "pizza"
}

# retrieve the mobile search results
result_mobile_json = serpwow.get_json(params_mobile)

# retrieve the tablet search results
result_tablet_json = serpwow.get_json(params_tablet)

# retrieve the desktop search results
result_desktop_json = serpwow.get_json(params_desktop)
```

## Parsing results
When making a request via the ``get_json`` method a standard Python ``dict`` is returned. You can inspect this dict to iterate, parse and store the results in your app.
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# make a simple query, returning JSON
serpwow = GoogleSearchResults("demo")
result = serpwow.get_json({ "q" : "pizza" })

# determine if the request was successful
success = result["request_info"]

if success:
  
  # extract the time taken and number of organic results
  time_taken = result["search_metadata"]["total_time_taken"]
  organic_result_count = len(result["organic_results"])

  # print
  print str(organic_result_count) + " organic results returned in " + str(time_taken) + "s"
```

## Paginating results, returning up to 100 results per page
Use the ``start`` and ``num`` parameters to paginate through Google search results. ``start`` is 0-based. The maximum number of results returned per page (controlled by the ``num`` param) is 100 (a Google-imposed limitation) for all ``search_type``'s apart from Google Places, where the maximum is 20. Here's an example.
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# request the first 100 results
serpwow = GoogleSearchResults("demo")
params = {
  "q" : "pizza",
  "start" : 0,
  "num": 100
}
result_page_1 = serpwow.get_json(params)

# request the next 100 results
params["start"] = 100
result_page_2 = serpwow.get_json(params)

# pretty-print the result
print "Page 1"
print json.dumps(result_page_1, indent=2, sort_keys=True)
print "Page 2"
print json.dumps(result_page_2, indent=2, sort_keys=True)
```

## Search example with all parameters
```python
from serpwow.google_search_results import GoogleSearchResults

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# set up a dict for the search parameters
params = {
  "q" : "pizza",
  "search_type" : "images",
  "gl" : "us",
  "hl" : "en",
  "location" : "New York,New York,United States",
  "google_domain" : "google.com",
  "time_period" : "custom",
  "sort_by" : "date",
  "time_period_min" : "02/01/2018",
  "time_period_max" : "02/08/2019",
  "device" : "mobile",
  "csv_fields" : "search.q,organic_results.position,organic_results.domain",
  "start" : "0",
  "num" : "100"
}

# retrieve the search results as CSV
result = serpwow.get_csv(params)

print result
```


## Locations API Example
The [Locations API](https://serpwow.com/docs/locations/overview) allows you to search for SerpWow supported Google search locations. You can supply the ``full_name`` returned by the Locations API as the ``location`` parameter in a Search API query (see [Searching with a location](https://github.com/serpwow/google-search-results-python#searching-with-a-location) example above) to retrieve search results geo-located to that location.
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# set up a dict for the location query parameters
params = {
  "q" : "mumbai"
}

# retrieve locations matching the query parameters as JSON
result = serpwow.get_locations(params)

# pretty-print the result
print json.dumps(result, indent=2, sort_keys=True)
```

## Account API Example
The [Account API](https://serpwow.com/docs/account/overview) allows you to check your current SerpWow usage and billing information. 
```python
from serpwow.google_search_results import GoogleSearchResults
import json

# create the serpwow object, passing in our API key
serpwow = GoogleSearchResults("demo")

# get our account info
result = serpwow.get_account()

# pretty-print the result
print json.dumps(result, indent=2, sort_keys=True)
```