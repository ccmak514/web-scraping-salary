# Web Scrape Salary Data of Data Analyst I in the USA from Salary.com
This project is to scrape the salary data of Data Analyst I in the USA from Salary.com.

On the page for the **Anchorage, Alaska**: https://www.salary.com/research/salary/benchmark/data-analyst-i-salary/anchorage-ak,
<br>
<br>
<img width="1035" alt="Screenshot 2023-07-31 at 2 00 45 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/0e3da094-72b8-4c9d-9a3e-e625007315db">
<br>
<br>
The 10th, 25th, 50th, 75th, and 90th percentile salary of Data Analyst I in the **red box** are the data that we want.

# Part 1: Get the URLs for All Cities
As we want to get the data from all the cities of the USA, we need to get the URLs by examining the https://www.salary.com/research/salary/select-location and get the relevant text to access the correct webpages for further web scraping.
<br>
<br>
<img width="899" alt="Screenshot 2023-07-31 at 2 10 08 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/b0ce4d2b-8577-4fd5-b5b5-6b2695420cc8">
<br>
<br>
# Part 2: Get the Data for Each City
After getting the relevant text to access the correct web pages, we can examine the data pattern in the HTML by `BeautifulSoup` and access the data by the `table` tag with the `table-chart` class, the `tr` tag, and `td` tag shown in the `web_scraping_salaries.ipynb`.

Store the data in a `pd.DataFrame` and save it in `.csv` format. For saving time, only the first 200 cities are considered for demonstration.
<br>
<br>
<img width="487" alt="Screenshot 2023-07-31 at 2 15 39 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/211642b1-ab9d-4dd1-b3bb-6e23549f9229">
