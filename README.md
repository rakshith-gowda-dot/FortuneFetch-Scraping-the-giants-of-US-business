# Largest US Companies by Revenue – Web Scraping & Data Cleaning

In this project, I performed web scraping using **BeautifulSoup** to extract the list of the largest companies in the United States by revenue from Wikipedia.  
The extracted data was cleaned, structured using **Pandas**, and saved as a CSV file for further analysis.

This project showcases skills in **web scraping**, **data cleaning**, and **data structuring** using Python.
<img width="1905" height="966" alt="Screenshot 2025-08-12 231451" src="https://github.com/user-attachments/assets/b089e5a2-2380-4303-93cf-21482efca11c" />
<img width="1416" height="750" alt="Screenshot 2025-08-12 231853" src="https://github.com/user-attachments/assets/80ed58cf-c20b-43eb-a876-a064b3603f3c" />



---

## Objective

To extract publicly available company data from Wikipedia, clean and organize it into a structured format, and store it for future use in analytics or reporting.

The focus was on:

- Extracting HTML table data from a webpage
- Cleaning and processing text data
- Structuring the data into a DataFrame
- Exporting the final dataset to CSV format

---

## Tools & Technologies Used

- **Python** – Core programming language  
- **BeautifulSoup (bs4)** – Web scraping HTML content  
- **Requests** – Fetching webpage data  
- **Pandas** – Data cleaning, structuring, and CSV export  

---

## Steps Involved

1. **Accessing the webpage** using the `requests` library  
2. **Parsing HTML content** with BeautifulSoup  
3. **Extracting table headers and rows** from the Wikipedia page  
4. **Cleaning text values** by removing extra whitespace and unwanted characters  
5. **Storing the data** in a Pandas DataFrame  
6. **Exporting the DataFrame** to a CSV file for future use  

---

## Code Snippet

python
from bs4 import BeautifulSoup
import requests
import pandas as pd

# Wikipedia URL
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'

# Fetch and parse the page
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html.parser')

# Extract table headers
world_table = soup.find('table', {'class': 'wikitable'})
world_table_titles = [header.text.strip() for header in world_table.find_all('th')]

# Create DataFrame
df = pd.DataFrame(columns=world_table_titles)

# Extract table rows
column_data = world_table.find_all('tr')
for row in column_data[1:]:
    row_data = row.find_all('td')
    individual_row_data = [data.text.strip() for data in row_data]
    df.loc[len(df)] = individual_row_data

# Save to CSV
df.to_csv(r'C:/Users/Rakshith/Downloads/Web_Scrapping.csv', index=False)
## 📌 What I Learned  
- Extracting and parsing HTML data with **BeautifulSoup**  
- Cleaning and transforming scraped data into structured formats  
- Using **Pandas** for DataFrame operations and CSV export  
- Understanding the workflow from raw web data to an analysis-ready dataset  

## 👤 About Me  
I am passionate about **data analytics, automation, and web scraping** to transform raw information into actionable insights.  
I enjoy building projects that combine **programming** and **real-world data applications**.  

🔗 **GitHub:** [github.com/rakshith-gowda-dot](https://github.com/rakshith-gowda-dot)  
🔗 **LinkedIn:** [linkedin.com/in/rakshith-n-81b34329a](https://linkedin.com/in/rakshith-n-81b34329a)  
