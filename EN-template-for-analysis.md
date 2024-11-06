**November 4th, 2024**<br>
**MPAD 2003**<br>
**Mark Talbot**<br>
**Presented to Jean-Sébastien Marier**<br>

# Exploring Service Requests By Ward

Use one hashtag symbol (`#`) to create a level 1 heading like this one.

## Foreword

For this assignment, you must extract data from a dataset provided by the instructor. You must then clean and analyze the data, create exploratory charts/visualizations, and find a potential story idea. Your assignment must clearly detail your process. You are expected to write about 1500-2000 words, and to include several screen captures showing the different steps you went through. Your assignment must be written with the Markdown format and submitted on GitHub Classroom.

I have been assigning different versions of this project to my digital journalism and data storytelling students for a few years now. Its structure was inspired by the main sections/chapters of [*The Data Journalism Handbook*](https://datajournalism.com/read/handbook/one/). This version was further inspired by the [Key Capabilities in Data Science](https://extendedlearning.ubc.ca/programs/key-capabilities-data-science) program offered by the University of British Columbia (UBC).

**Here are some useful resources for this assignment:**

* [GitHub's *Basic writing and formatting syntax* page](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [The template repository for this assignment in case you delete something by mistake](https://github.com/jsmarier/jou4100_jou4500_mpad2003_project2_template)

Did you notice how to create a hyperlink? In Markdown, we put the clickable text between square brackets and the actual URL between parentheses.

And to create an unordered list, we simply put a star (`*`) before each item.

## 1. Introduction

I’m working with a dataset of service requests in Ottawa from August of 2024 and in this assignment, I will analyze the data by ward. I will figure out which wards have a high and low volume of requests, and further break down the most common types of requests, which will help identify local issues. Lastly, I can investigate which issues are ongoing and which are resolved. For this project, I'm using a subset of a larger dataset published by the city of Ottawa. The subset was provided to me by my instructor in a CSV file.
* The link to the original dataset is https://open.ottawa.ca/documents/65fe42e2502d442b8a774fd3d954cac5/about
* The link to the subset is https://raw.githubusercontent.com/jsmarier/course-datasets/refs/heads/main/ottawa-311-service-requests-august-2024.csv

The main sections covered in this assignment will include getting data, understanding data, and finding a potential story.


## 2. Getting Data

### importing the data into Google Sheets
My first step in importing the data into Google Sheets was to open the dataset. Once it was open I right-clicked on “save as”, and saved it to the folder I created for this project as a CSV file. Next, I had to upload the CSV file to my Google Drive. In my drive, at the top left corner, I clicked new, then file upload. I selected the CSV file from my folder and it uploaded to my drive. Lastly, I opened a new Google sheet and selected file, import, then chose the file I just uploaded and then hit insert. Under import location I selected “create new spreadsheet” and under separator type, I chose Comma as the delimiter in this file is a comma. I clicked on import data and once it finished creating the spreadsheet I clicked the link that said “open now”.


### Screenshot of the data in google sheets.
![](DataScreenshot.png)<br>
*Figure 1: The first 24 rows of the dataset in google sheets*

### The link to the google sheet dataset is https://docs.google.com/spreadsheets/d/1DqXQppzhMtfShrCygnySmZeWHvo04dcBQtIBluwdadQ/edit?gid=2014664155#gid=2014664155 

There are 11 different data types in the set each with their own column, as well as 28,538 recorded service requests. The data is not very clean as many columns, primarily address, longitude, and latitude, have missing values, and some cells are not aligned with other cells in their same column. 
* Column K uses nominal variables with the different ways services were requested. 
* Column B also uses nominal variables to signify the status of the request. 
* In columns E and F interval variables are used to represent the date that the request was opened and closed. Some data points in the closed column are missing. 

### Sugested improvments
For people to better understand the wards and their location it would be helpful to add the name of the ward inside the column alongside the number, as well as to add another column with the councilor’s name. This will give readers a clearer context to the location of these requests as opposed to trying to figure out ward numbers and coordinates which many people dont know.

### Question
How does the volume of service requests vary from ward to ward?

## 3. Understanding Data

### 3.1 VIMO Analysis
* **Valid**
 Column B: All data in this column was valid, it was accurate, complete, and consistent with expected values. Each of the rows had one of three options of the status being active, resolved or cancelled.
* **Invalid**
Column E: This column contained Invalid data as the last request in the dataset was made on September 1st. This is after the August time frame so it is inconsistent with the rest of the data.
* **Missing**
Columns G, H, I: Missing Data is frequent in these three columns, they all relate to the location of the request so it is apparent that finding the location of the request was difficult. in Column I there are 1,549 missing data points but that is nothing compared to the 24,128 missing coordinates in columns G and H.
* **Outlier**
Column K: This column shows the channel of how the request was received. The outliers for this were the requests by counter as only 2 requests were by this channel.

### 3.2 Cleaning data
#### Split Function

1. I decided I wanted to `split` the description to get rid of the french version.
2. I right-clicked on the description column and hit “add column left” to add two new columns.
3. In the first column I wrote the function `[=SPLIT(D2,"|")]`. The "|" sets the separator to thst character.
4. In the bottom right corner of the cell I put the function in, there is a circle. I dragged the circle down to the end of the datasheet to replica the split function for the rest of the column.
5. I then copied and pasted values only. 
6. Lastly, I deleted the old description with both languages and the new column with just French.

#### Whitespace Function
To clear the white space from each cell in the dataset i followed these steps.
1. I selected the entire dataset by clicking on the block to the left of column A and on top of column 1
2. I then went to the data tab at the top of the screen and clicked on data cleanup.
3. From there 3 options showed up, I clicked “trim whitespace”


#### Concatenate function

I wanted to merge the latitude and longitude to make one column called coordinates. The steps to do so are as follows.
1. I right-clicked on the column with latitude and selected add column left
2.  I then typed my title for the column which was “Coordinates”
3. I then implemented the Concatenate tool into row 1 of the new column and wrote the following function `=CONCATENATE(I2,", ",J2)`
4. A suggestion box popped up for the rest of the column to replicate the function so I accepted however, if that doesn’t show up you must do the same thing as the `split` function. You drag down from the corner of the cell until you reach the end of the column.
5. I copied the new column and went to the edit tab, then clicked paste special, and values only
6. Lastly, I deleted the two original columns of latitude and longitude.

If you name a function, put it between "angled" quotation marks like this: `IMPORTHTML`.

If you want to include the entire line of code, do the same thing, albeit with your entire code: `=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)`.

Alternatively, you can put your code in an independent box using the template below:

``` r
=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)
```
This also shows how to create an ordered list. Simply put `1.` before each item.


Support your claims by citing relevant sources. Please follow [APA guidelines for in-text citations](https://apastyle.apa.org/style-grammar-guidelines/citations).

**For example:**

As Cairo (2016) argues, a data visualization should be truthful...


### 3.3. Exploratory Data Analysis (EDA)

I chose these variables because I feel they offer a great way to analyze the data. By sorting the number of requests by ward it allows us to see which wards have a high volume of service requests and which have lower volume. If this data were to be replicated for future months, it would be a good indicator of trends within the wards to see if there have been less or more service requests made in the last month.

An interesting statistic that stands out is that ward 12, Rideau-Vanier, has the most service requests in the Ottawa area. This ward had a total of 1,628 requests which is 57 more requests than ward 14, in second place.

This graph can provide us with a story that some wards need to have their resource allocation adjusted based on how many requests they receive. For wards with many requests, they could receive more personnel and equipment to better suit their community. The same applies to wards with low requests, they could have some of thor resources distributed to other wards.

An easy number that would warrant further investigation is the fact that there are 1,549 requests that arent assigned to a ward. Depending on where these requests came from it could massively skew the data and change the narrative.


![](pivot_Table.png)<br>
*Figure 2: This pivot table shows the realtionship between the ward number and the toal number of service requests*

**This section should also include a screen capture of your exploratory chart, like so:**

![](Service_Requests_by_Ward.png)<br>
*Figure 3: This column chart shows the total number of service requests by ward*

## 4. Potential Story

Insert text here.

## 5. Conclusion

Insert text here.

## 6. References

Include a list of your references here. Please follow [APA guidelines for references](https://apastyle.apa.org/style-grammar-guidelines/references). Hanging paragraphs aren't required though.

**Here's an example:**

Bounegru, L., & Gray, J. (Eds.). (2021). *The Data Journalism Handbook 2: Towards A Critical Data Practice*. Amsterdam University Press. [https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153](https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153)
