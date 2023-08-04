# Web Scraping and EDA of Salary Data of Data Analyst I in the US

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

------------------------------------------
### <b>1. Get the URLs of All Cities</b>

First, examine https://www.salary.com/research/salary/benchmark/data-analyst-i-salary/juneau-ak.
<br><br>By observation, only the last part <font color=red>(juneau-ak)</font> of the URLs determines which city we are considering and we need to get this text for all cities for further web scraping.
<br><br>Therefore, inspect https://www.salary.com/research/salary/select-location and scrape the required text.

<br>
<img width="899" alt="Screenshot 2023-07-31 at 2 10 08 PM" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/b0ce4d2b-8577-4fd5-b5b5-6b2695420cc8">
<br><br>

-------------------------------------------
### <b>2. Get the Data of All Cities</b>

After getting the relevant text to access the correct web pages, we can examine the data pattern in the HTML by `BeautifulSoup` and access the data by the `table` tag with the `table-chart` class, the `tr` tag, and `td` tag shown in the `web_scraping_salaries.ipynb`.

Store the data in a `pd.DataFrame` and save it in `.csv` format.
<br>
<br>
<img width="554" alt="salary" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/b7010191-f18f-43dd-821c-08bde8881a08">
<br><br>

--------------------------------------------
### <b>3. Data Preprocessing for EDA</b>

After dropping missing data, scrape the corresponding regions of each state from https://www.mappr.co/political-maps/us-regions-map/ and store them in a dictionary `dict_state_region`. 

The screenshot of https://www.mappr.co/political-maps/us-regions-map/ is as follows:

<img width="719" alt="state_region" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/0f874edc-07d6-4e9f-8698-3e26e3485158">
<br><br>

Use `.map` to map the value in `state` to the `region` according to the `dict_state_region` and save it in `.csv` format.
<br><br>

<img width="611" alt="salary_renewed" src="https://github.com/ccmak514/web-scraping-salary/assets/101066418/26467890-f8c4-48a9-96e4-a91cc0f12103">
<br><br>

---------------------------------
### <b>4. EDA - General</b>

First take a look to the distributions of 10th, 25th, 50th, 75th and 90th percentiles of 800 cities by plotting histograms (`sns.histplot`) and the relationship between each percentile by pairplot (`pairplot`).

The **histograms** are as follows:
![histograms](https://github.com/ccmak514/web-scraping-salary/assets/101066418/1a88f081-60f6-4ffd-9388-3b664e9e31ea)

The **pairplot** is as follows:
![pairplot](https://github.com/ccmak514/web-scraping-salary/assets/101066418/3f7e3699-71c7-4525-a1ff-85ef3c50e4d4)
<br>
The distribution of 10th, 25th, 50th, 75th and 90th percentiles of 800 cities are almost the <font color=red><b>same</b></font> and there is only <font color=red><b>right shifting</b></font> between the distributions. When one of the percentile increases, other percentile increases linearly. It is trivial according to the definitions of percentiles.
<br><br>
The **bar chart of states of the US** are as follows:
![bar_states](https://github.com/ccmak514/web-scraping-salary/assets/101066418/7501e8f1-a48a-47b9-87e6-44190a2590e3)

The **bar chart of regions of the US** are as follows:
![bar_region](https://github.com/ccmak514/web-scraping-salary/assets/101066418/ded5bbfa-adde-4089-aa20-a7700097e801)
<br>
In this data set, most cities are located in <font color=red><b>CA (California) state</b></font> and in the <font color=red><b>Northeast region</b></font>. To get more insights, data should be further analysed from the perspective of <font color=red><b>regions</b></font> and <font color=red><b>states</b></font>

------------------------------------
### <b>5. EDA - Regions</b>

To find out the relationship between regions and percentiles, a <font color=red>**pivot table**</font> is made and the percentiles are aggregated for each region by `np.mean`. A <font color=red>**heatmap**</font> is for visualizing the pivot table and <font color=red>**boxplots of 50th percentiles of 6 regions**</font> are for studying the <font color=red>**underlying distribution**</font> of each region. For simplicity, <font color=red>**only**</font> boxplots of 50th percentiles are used.</font>

![heatmap_boxplots_region](https://github.com/ccmak514/web-scraping-salary/assets/101066418/e285f0b9-358c-42a6-a3ef-f3c824da62b5)
<br>
According to the heatmap, the mean of all percentiles of <font color=red>**District of Columbia**</font> (which is stands for the only data, <font color=red>**Washington, D.C.**</font>) <font color=red>**outperforms**</font> other regions, while the mean of all percentiles of the <font color=red>**Southeast region**</font> is the <font color=red>**lowest**</font>. 
<br><br>
According to the boxplots, the Data Analyst I with the <font color=red>**highest 50th percentile salary**</font> works in the <font color=red>**West region**</font> and the <font color=red>**spread**</font> of salary in the <font color=red>**West**</font> region is the <font color=red>**largest**</font>.

--------------------------------------------------
### <b>6. EDA - States in each Region</b>

**Heatmap and Boxplots for States in the Northeast Region**:
![heatmap_boxplots_NE](https://github.com/ccmak514/web-scraping-salary/assets/101066418/1e578a95-b54a-459c-99ae-db9df375129b)
<br>
According to the heatmap, the mean of all percentiles of <font color=red>**NJ**</font> state (<font color=red>**New Jersey**</font>) <font color=red>**outperforms**</font> other states, while the mean of all percentiles of the <font color=red>**ME**</font> state (<font color=red>**Maine**</font>) is the <font color=red>**lowest**</font>. The <font color=red>**spread**</font> of salary in the <font color=red>**NJ**</font> state (<font color=red>**New Jersey**</font>) is <font color=red>**moderate**</font>, while the <font color=red>**spread**</font> of salary in the <font color=red>**NY**</font> state (<font color=red>**New York**</font>) is the <font color=red>**largest**</font>.
<br><br><br>
**Heatmap and Boxplots for States in the West Region**:
![heatmap_boxplots_W](https://github.com/ccmak514/web-scraping-salary/assets/101066418/5cb057e0-7244-458a-b5a2-51684b50df06)
<br>
According to the heatmap, the mean of all percentiles of <font color=red>**CA**</font> state (<font color=red>**California**</font>) <font color=red>**outperforms**</font> other states, while the mean of all percentiles of the <font color=red>**MT**</font> state (<font color=red>**Montana**</font>) is the <font color=red>**lowest**</font>. The <font color=red>**spread**</font> of salary in <font color=red>**most**</font> of the state in <font color=red>**West**</font> region is <font color=red>**moderate**</font>, and the Data Analyst I with the <font color=red>**highest salary**</font> works in the <font color=red>**CA**</font>. The 50th percentile of salary in <font color=red>**CA**</font> state can be higher than <font color=red>**80000 USD**</font>.
<br><br><br>
**Heatmap and Boxplots for States in the Midwest Region**:
![heatmap_boxplots_MW](https://github.com/ccmak514/web-scraping-salary/assets/101066418/269d4532-cac0-4f55-be4f-b08ccbd0ef4a)
<br>
<font size=4>According to the heatmap, the mean of all percentiles of <font color=red>**MN**</font> state (<font color=red>**Minnesota**</font>) <font color=red>**outperforms**</font> other states, while the mean of all percentiles of the <font color=red>**SD**</font> state (<font color=red>**South Dakota**</font>) is the <font color=red>**lowest**</font>. 
The <font color=red>**spread**</font> of salary in <font color=red>**most**</font> of the state in <font color=red>**Midwest**</font> region is <font color=red>**moderately high**</font>, and <font color=red>**all**</font> the <font color=red>**50th percentile of salary**</font> in the <font color=red>**SD**</font> state is lower than <font color=red>**60000 USD**</font>.
</font>
<br><br><br>
**Heatmap and Boxplots for States in the Southeast Region**:
![heatmap_boxplots_SE](https://github.com/ccmak514/web-scraping-salary/assets/101066418/3e04b493-93cb-4d9c-a24b-8cc422d4cd30)
<br>
<font size=4>According to the heatmap, the mean of all percentiles of <font color=red>**VA**</font> state (<font color=red>**Virginia**</font>) <font color=red>**outperforms**</font> other states, while the mean of all percentiles of the <font color=red>**MS**</font> state (<font color=red>**Mississippi**</font>) is the <font color=red>**lowest**</font>. 
Except the <font color=red>**VA**</font> state, the <font color=red>**spread**</font> of salary of <font color=red>**most**</font> of the state in <font color=red>**Southeast**</font> region is <font color=red>**moderate**</font> and only Data Analyst I's <font color=red>**50th percentile**</font> salary of <font color=red>**VA**</font> state in <font color=red>**Southeast region**</font> can be higher than <font color=red>**70000 USD**</font>.
</font>
<br><br><br>
**Heatmap and Boxplots for States in the Southwest Region**:
![heatmap_boxplots_SW](https://github.com/ccmak514/web-scraping-salary/assets/101066418/d8825819-cde3-4976-aa44-5765eabb652f)
<br>
According to the heatmap, the mean of all percentiles of <font color=red>**AZ**</font> state (<font color=red>**Arizona**</font>) <font color=red>**outperforms**</font> other states, while the mean of all percentiles of the <font color=red>**NM**</font> state (<font color=red>**New Mexico**</font>) is the <font color=red>**lowest**</font>. 
The <font color=red>**spread**</font> of salary in the <font color=red>**AZ**</font> state (<font color=red>**Arizona**</font>) is <font color=red>**lowest**</font>, while the <font color=red>**spread**</font> of salary in the <font color=red>**TX**</font> state (<font color=red>**Texas**</font>) is <font color=red>**highest**</font>.
<br><br><br>
**Heatmap and Boxplots for States in the Washington, D.C.**:
![heatmap_boxplots_DC](https://github.com/ccmak514/web-scraping-salary/assets/101066418/bb6277d7-d809-45c2-b6e7-93b76652eb73)
<br>
There is only <font color=red><b>one data</b></font> in <font color=red><b>District of Columbia</b></font> and it stands for the <font color=red><b>Washington, D.C.</b></font> city. The mean of all percentiles <font color=red><b>outperforms</b></font> all the states in all regions according to the heatmap in <font color=red><b>Section 5</b></font>. 
However, some Data Analyst I in <font color=red><b>West and Northwest regions</b></font> gain higher salary (50th percentiles) according to Section 5. More data is required for better analysis.
