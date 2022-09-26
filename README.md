# Market Price Web Scraping

## Why Web Scrapping

Price scraping is rising with the growing competition and growth in online marketplaces. A new player in the market can quickly get up to speed using price and content scraping services. This is because when scraper bots attack a website, they potentially gain access to information on Stock Keeping Units (SKU), product listings, historical pricing, and their entire product catalog. This breadth of information can give new rivals a huge competitive edge. Competitors can automate their scraping activity to such an extent that their website automatically reflects the best price upon analyzing prices from competing sites.

 ### However, it´s not possible to scrape all the data with website APIs.
Some websites provide APIs for users to access part of their data. But even though these sites provide APIs, there still exist some data fields that can´t scrape or have no authentication to access.

For example, Amazon provides a Product Advertising API, but the API itself couldn’t provide access to all the information displayed on its product page for people to scrape, like price and others. In this case, the only way to scrape more data, saying the price data field, is to build our scraper by programming or using certain kinds of automated scraper tools.
 
### It is hard to get the correct data, even for programmers.
Sometimes, even if we know how to scrape data on our own by programming, like the example below in Python, we still could not scrape data successfully for various reasons. In most cases, we probably would be forbidden to scrape from certain websites due to our suspicious repeating scraping actions within a short time. 

### Why I started this project
Consumers nowadays are constantly looking for discounts, special offers, and comparing prices in different online businesses. I started this project for personal use and to help me in a very specific scenario where I usually compare the prices between multiple websites and make a decision on where I will buy the products. This was a weekly activity and manual. 

To improve the work and study a little bit more about data manipulation, data analysis, etc, I tested this model to scrap data from the web and help to increase much time on my weekly activity. It would be best if the website is up to date on pricing and if all the markets allow you to scrap the data, but this is not the case and this entire automation is used today for a learning perspective and try to solve many different problems on the way.

## Libraries for data exploration, processing, and web scraping

We need to import a couple of Python libraries that we will need for data exploration, processing, visualization, and web scraping.

- **Pandas** — We will be using pandas data frames for their functions and a tabular representation of our dataset.

- **BeautifulSoup** — For parsing HTML and XML documents. We will be using this library for web scraping.

- **requests**- To download the web page in HMTL format.

- **re** - Work with Regular Expressions

- **json** - Convert string to json obejct

We will be working in the Google Colab for this tutorial, but you are welcome to use a Python IDE of your choice.

Additionally, we are using the **print_function** library and redefined the work for the **print** command to improve the logging and debugging on the Google Colab.


## Set some reusable parameters

The following parameters are reusable in the processes. 
- `enable_print` - log the print when this parameter is `True`
- `filename` - import and export the CSV data with the Product and the prices after web scrapping.

## Defined the functions

At this point we are working with two types of functions:
- Utility functions -  can be easily copied for other projects without changes based on the use.
- Custom-Specific functions - Necessary to update the code, and logic, and these functions are very specific to solve/get the requirement completed.

### Utilities Functions

#### print functoin
If the parameter `enable_print` is `True` the `print` will be used to log information and help to debug the application.

#### compare_price
this function just compares two prices and provides status about the comparison

### Custom-Specific Functions per Market
To test the application I tried to scrap the data from some marketplaces, but for some without success. 
- St Marche
- Oba
- Hakuo
- Sams Club
- Pão de Açucar

## Load and work with CSV data

Now, after the import of the main libraries and defining the functions, the next step is to work with the data. 

To easily store the data somewhere that can be used for offline manipulation in Excel the decision was to use Google Drive to store a CSV.


### Fix the Prices format 
Due to Excel formation for localization currencies, I had to perform some string manipulation before starting to work with the data on JSON objects. Doing this manipulation before creating the JSON object avoids manipulating the data many times under the custom-specifics functions.


### Working with JSON objects
After all the manipulations were completed in the previous step we are good to create the JSON objects and easily work with the data. 

### Iterate each record line
For each record, the CVS/JSON checks if it has the URL to perform the request and calls the market specif function to extract the `product name`, `price`, `size`, etc.


### Update the Data Frame and Export the Data
The JSON object `data` is getting updated from the market-specific functions with `price`, `size`, etc. At this time we are converting back the JSON object to Pandas DataFrame and updating the original DataFrame with the new data.

#### Export the data for a local Excel data manipulation
By using the same Google Drive integration with the previous CSV file, now we are updating the file with new data. Using the same file we can compare the old prices and set some status for each record.

## Data classification and visualization

The first data visualization is related to *On Sale* products ordered by *Market*
