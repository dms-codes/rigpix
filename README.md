# Web Scraping with BeautifulSoup

This Python script demonstrates how to perform web scraping using BeautifulSoup to extract data from a webpage. In this example, we scrape data from the [RigPix](http://www.rigpix.com/icom/icomselect.htm) website, specifically the Icom radio models and their corresponding details.

## Prerequisites

Before running the script, ensure you have the required libraries installed. You can install them using `pip`:

```bash
pip install pandas requests beautifulsoup4
```

## Usage

1. Import the necessary libraries:

   ```python
   import pandas as pd
   import requests
   from bs4 import BeautifulSoup
   ```

2. Specify the URL of the webpage you want to scrape:

   ```python
   url = "http://www.rigpix.com/icom/icomselect.htm"
   ```

3. Send an HTTP GET request to the URL and parse the HTML content using BeautifulSoup:

   ```python
   r = requests.get(url)
   soup = BeautifulSoup(r.text, 'html.parser')
   ```

4. Identify the HTML elements that contain the data you want to extract. In this script, we find all `h3` headers:

   ```python
   headers = soup.find_all('h3')
   ```

5. Extract the headers into a list:

   ```python
   headers_list = []
   for h in headers:
       headers_list.append(h.text)
   ```

6. Create a dictionary to store the scraped data:

   ```python
   data = {}
   ```

7. Use Pandas to parse the HTML tables on the webpage and store them in a list:

   ```python
   df_list = pd.read_html(r.content)
   ```

8. Populate the `data` dictionary with the scraped data, using the headers as keys:

   ```python
   for i, l in enumerate(df_list[3:]):
       data[headers_list[i]] = l
   ```

9. Print or further process the extracted data. In this script, we print the `data` dictionary:

   ```python
   print(data)
   ```

## Example

The script retrieves information about Icom radio models and stores it in a dictionary, making it easy to work with the data programmatically.

## License

This script is provided under the [MIT License](LICENSE).
```

Feel free to customize the README.md file further to include additional information or usage examples for your specific project.
