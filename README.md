![Logo](https://hernebaydomestics.co.uk/wp-content/uploads/2020/09/Samsung-QE49Q80TATXXU-Display.jpg)
    
# Amazon Web Scraping Using Python

In this project, We are going to webscrape Amazon for a TV using Python.


## Authors

- [@jkawalec](https://www.github.com/jkawalec)

  
## Installation
Used Jupyter Notebook for this project.

Download Anaconda here: https://www.anaconda.com/products/individual#Downloads

Download project here: https://github.com/jkawalec/Web-Scraping-Using-Python/blob/main/Amazon%20TV%20web%20Scrape.ipynb

Website URL Scraped: https://www.amazon.com/SAMSUNG-55-Inch-Crystal-AU8000-Built/dp/B08Z21BBWK?ref_=Oct_d_onr_d_172659&pd_rd_w=gXlr1&pf_rd_p=f2b556d9-2905-446e-a142-cdce50e9497c&pf_rd_r=SJP2GP3ETTXAW7JH754J&pd_rd_r=d8c22561-2605-4a11-95c7-64c13cfaf930&pd_rd_wg=x6fDJ&pd_rd_i=B08Z21BBWK

Import libraries needed

```bash
from bs4 import BeautifulSoup as bs
import requests
import smtplib
import time
import datetime
import pandas as pd
import csv
```
    
## Usage

Use this project to web scrape a specific item page on a website. I only used this to scrape one specific item, but it can be expanded on to scrape more across websites.


```javascript
header = ['title', 'price','Date']
data = [title, price,today]

with open('Amazontv.csv','w',newline='',encoding='UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(header)
    writer.writerow(data)
```

```javascript
url = 'https://www.amazon.com/SAMSUNG-55-Inch-Crystal-AU8000-Built/dp/B08Z21BBWK?ref_=Oct_d_onr_d_172659&pd_rd_w=gXlr1&pf_rd_p=f2b556d9-2905-446e-a142-cdce50e9497c&pf_rd_r=SJP2GP3ETTXAW7JH754J&pd_rd_r=d8c22561-2605-4a11-95c7-64c13cfaf930&pd_rd_wg=x6fDJ&pd_rd_i=B08Z21BBWK'
headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}

page = requests.get(url,headers=headers)

soup1 = bs(page.content, "html.parser")

soup2 = bs(soup1.prettify(), "html.parser")

title = soup2.find(id='productTitle').get_text()

price = soup2.find(id='priceblock_ourprice').get_text()

print(title) 
print(price)
```
