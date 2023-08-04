# Web Scrape Salary Data of Data Analyst I in the USA from Salary.com

#### <b>Introduction:</b><br>

For those who would like to become a data analyst in the US, it is important to do a data analysis about the salary.
<br><br>
In this project, the <font color=red>**10th, 25th, 50th, 75th and 90th percentiles**</font> of salary of <font color=red>**Data Analyst I**</font> in 800 cities in the US are collected by web scraping. After getting the data, perform <font color=red>**EDA (Exploratory Data Analysis)**</font> after data preprocesssing to find out the insights from the data by <font color=red>**visualization (bar chart, histogram, heatmap, pairplot, boxplot)**</font>.

#### <b>Table of Contents:</b><br>

&nbsp;&nbsp;&nbsp;&nbsp;1. Get the URLs of All Cities<br>
&nbsp;&nbsp;&nbsp;&nbsp;2. Get the Data of All Cities<br>
&nbsp;&nbsp;&nbsp;&nbsp;3. Data Preprocessing for EDA<br>
&nbsp;&nbsp;&nbsp;&nbsp;4. EDA - General<br>
&nbsp;&nbsp;&nbsp;&nbsp;5. EDA - Regions<br>
&nbsp;&nbsp;&nbsp;&nbsp;6. EDA - States in each Region<br>
<br>
On the page for the **Anchorage, Alaska**: https://www.salary.com/research/salary/benchmark/data-analyst-i-salary/anchorage-ak,
<br>
<br>
<img width="1035" alt="Screenshot 2023-07-31 at 2 00 45 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/0e3da094-72b8-4c9d-9a3e-e625007315db">
<br>
<br>
The 10th, 25th, 50th, 75th, and 90th percentile salary of Data Analyst I in the <font color=red><b>red box</b></font> are the data that we want.
<br><br>

### <b>1. Get the URLs of All Cities</b>

First, examine https://www.salary.com/research/salary/benchmark/data-analyst-i-salary/juneau-ak.
<br><br>By observation, only the last part <font color=red>(juneau-ak)</font> of the URLs determines which city we are considering and we need to get this text for all cities for further web scraping.
<br><br>Therefore, inspect https://www.salary.com/research/salary/select-location and scrape the required text.

<br>
<img width="899" alt="Screenshot 2023-07-31 at 2 10 08 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/b0ce4d2b-8577-4fd5-b5b5-6b2695420cc8">
<br><br>

### <b>2. Get the Data of All Cities</b>

After getting the relevant text to access the correct web pages, we can examine the data pattern in the HTML by `BeautifulSoup` and access the data by the `table` tag with the `table-chart` class, the `tr` tag, and `td` tag shown in the `web_scraping_salaries.ipynb`.

Store the data in a `pd.DataFrame` and save it in `.csv` format.
<br>
<br>
<img width="487" alt="Screenshot 2023-07-31 at 2 15 39 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/211642b1-ab9d-4dd1-b3bb-6e23549f9229">
<br><br>

### <b>3. Data Preprocessing for EDA</b>
