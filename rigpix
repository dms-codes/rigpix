import pandas as pd
import requests
from bs4 import BeautifulSoup


url = "http://www.rigpix.com/icom/icomselect.htm"

r = requests.get(url)
soup = BeautifulSoup(r.text, 'html.parser')

headers = soup.find_all('h3')

headers_list = []
for h in headers:
    headers_list.append(h.text)

data = {}

df_list = pd.read_html(r.content) # this parses all the tables in webpages to a list
for i,l in enumerate(df_list[3:]):
    data[headers_list[i]] = l

print(data)


