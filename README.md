# Miniproject 2

### [Assignment](assignment.md)

## Project/Goals
The main goal of this project is to collect information on different points of interest (POIs) using two APIs using ```Python```, namely [Foursquare](https://developer.foursquare.com/reference/place-search) and [Yelp](https://www.yelp.com/developers/documentation/v3/business_search). Latitude and longitude were used to define the location ([Downtown Kingston](https://www.google.com/maps/@44.232459,-76.4858185,21z), Ontario).

We will also be using the collected data to create tables in an SQL database using ```SQLite3```. Data manipulation from these tables will be done using ```Python``` and the ```pandas``` package.

## Process
### Familiarization with API documentation
The first step involved browsing through the API documentation to check what information was required in our GET requests. [Foursquare](https://developer.foursquare.com/reference/place-search) and [Yelp](https://www.yelp.com/developers/documentation/v3/business_search) have well written documentation, so once the user has an API key, it is easy to start sending requests. 

### Sending requests to the API
Requests were sent by using the ```requests``` package. To avoid sending several requests unnecessarily, the text from the GET response was stored as a JSON file. This was done for both APIs.

### Parsing through the data
To parse through the response object, the ```JSON``` and ```pprint``` packages were used. It was found that the response file was a nested dictionary. After some browsing, empty lists and a for loop was used to extract the data from the JSON file. The same approach was used for both APIs

### Creating the ```DataFrame```
Dictionaries were created using the lists generated in the previous step. A dictionary was chosen because this data type can easily be ported into a ```DataFrame```. An example of the output is shown below.  
![alt text](/home/eduardo/lighthouse-data-notes/mini-project-II/images/df-ouput.png)

### Creating a database using ```SQLite3```
Following that, a database was created using the ```SQLite3``` package. Once the ```DataFrames``` were pushed to the database using the ```to_sql()``` method, the data could be accessed by using the ```read_sql()``` method.


## Results
(fill in what you found about the comparative quality of API coverage in your chosen area)

## Challenges 
The main challenge for me was parsing through the JSON response object. There are different tools to help us navigate this challenge, such as the pandas ```normalize()``` method. I chose to navigate the nested dictionary using indexing and for loops, but ```normalize()``` might be a faster way of transferring the JSON data to a pandas ```DataFrame```.

Another challenging part was figuring out how to work with the tables using pandas. Before using the ```read_sql()``` method, I spent a significant time trying to come up with ways to extract the data from our database. 

## Future Goals
In the future, I would like to compare the results from these two APIs with the Google Places API. Google Maps is one of the most popular apps for navigation, so it is updated more frequently. 