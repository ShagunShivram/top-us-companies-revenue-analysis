Top U.S. Companies by Revenue (Web Scraping + Visualization)

This project scrapes the Wikipedia page of the largest companies in the United States by revenue using Python.
It cleans and analyzes the data using Pandas, and visualizes the Top 10 companies using Matplotlib.

A.Project Overview:

Data Source: Wikipedia (https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue)
Tools Used: requests, pandas, matplotlib
Objective: Demonstrate data scraping, cleaning, and visualization in Python.

B.Workflow:

Fetch data from Wikipedia using the requests library.
Parse HTML tables using pandas.read_html().
Clean and standardize column names.
Convert revenue to numeric values.
Visualize the top 10 companies by revenue.

C.Code Example:

import requests
import pandas as pd
import matplotlib.pyplot as plt

url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)',
    'Accept-Language': 'en-US,en;q=0.9',
    'Referer': 'https://www.google.com'
}

resp = requests.get(url, headers=headers)
html = resp.text

tables = pd.read_html(html)
df = tables[0]
df.columns = df.columns.str.strip().str.lower()
df['revenue (usd millions)'] = pd.to_numeric(df['revenue (usd millions)'], errors='coerce')

top10 = df.head(10)
plt.figure(figsize=(10,6))
plt.barh(top10['name'], top10['revenue (usd millions)'], color='teal')
plt.gca().invert_yaxis()
plt.title('Top 10 U.S. Companies by Revenue (in millions USD)', fontsize=14, weight='bold')
plt.xlabel('Revenue (USD millions)')
plt.ylabel('Company')
plt.tight_layout()
plt.show()

D.Output Example:

A horizontal bar chart showing the top 10 U.S. companies by revenue.





















































































































