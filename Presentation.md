---
marp: true
theme: uncover
paginate: true
image :
---

# Scrapper

Scrapper is a web scrapper that can scrape and extract information from any website. It's designed to be fast and efficient, making it easy for you to gather the data you need quickly and easily.Specifically it is designed for [E.Leclerc](https://www.e.leclerc/) and more specifically for scraping details of all the products of [Sports section](https://www.e.leclerc/cat/sport-loisirs) and [Jwellery section](https://www.e.leclerc/cat/vetements).
The data is stored locally on the mongodb database and some Queries are created to analyze the data.

## Approach

+ Since the website [E.Leclerc](https://www.e.leclerc/) uses the dynamic data loading techniques using javascript, thus the whole idea was just to inspect the XHR.

+ Lets see what we can get on inpecting the [sport page](https://www.e.leclerc/cat/sport-loisirs)

![](image1.png)

+ As you can see all the subcategories of the sport are denoted as childrens, sof all the data regardign the subcategories can be obtained here only

+ From here we go on the subcategories and so on

+ since there is pagination, so to handle this i used the mathmatical startegy of taking ceil of the total product number divided by 90, thus getting the total number of pages needed to be traversed in that sub category.

![](image2.png)

+ For accessing the product page , we need the SKU number, hence by using that i was able to navigate on the product page.

+ Now for the prodcut page after inspecting it , the structure looked like as shown in below figure

![](image3.png)

+ Thus overall 4 parsing functions needed in total out of them three are the callback functions.

---


### Working

1. Now all the prerequistes are fixed, we need to run the scrapy spider to crawl and scrap the data, it takes around 45 - 50 minutes to scrap all the data of sports section and jwellery section.

2. Now run the following commands and wait for approx 40 - 50 minutes to finish the process of scraping all the data
    ```
    cd scrap_Eleclerc
    scrapy crawl scrapit
    ```

3. Now, In the same directory there is the file ```runQuery.py``` one can write the query there and run the file py wrting the command 
    ```
    python runQuery.py
    ```

4. The result of Query will be output on the terminal
## Built With

- [Python](https://www.python.org/)
- [scrapy](https://scrapy.org/)
- [Pymongo](https://pypi.org/project/pymongo/)
- [MongoDB](https://www.mongodb.com/)

```
## Folder structure 

scrap_Eleclerc
├── scrap_Eleclerc
│   ├── __init__.py
│   ├── items.py
│   ├── middlewares.py
|   ├── pipelines.py
│   └── settings.py
|
└── runQuery.py
|
└── scrapy.cfg
|
└── README.md

```
+ Items.py is as shown below contains the details about the product that we need to store and be accessed using the container.

![](image4.png)

+ pipeline.py is as shown below is used to establish the connection between the database and the spider.

![](image5.png)
---


---
+ The main file inside the spider folder, the scrapit.py is the main parsing file, that is visiting all the pages and parsing the data in those pages

![](Image6.png)











