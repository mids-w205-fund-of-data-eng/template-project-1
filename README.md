# Project 1: Query Project

- In the Query Project, you will get practice with SQL while learning about
  Google Cloud Platform (GCP) and BiqQuery. You'll answer business-driven
  questions using public datasets housed in GCP. To give you experience with
  different ways to use those datasets, you will use the web UI (BiqQuery) and
  the command-line tools, and work with them in jupyter notebooks.

#### Problem Statement

- You're a data scientist at Lyft Bay Wheels (https://www.lyft.com/bikes/bay-wheels), formerly known as Ford GoBike, the
  company running Bay Area Bikeshare. You are trying to increase ridership, and
  you want to offer deals through the mobile app to do so. What deals do you
  offer though? Currently, your company has several options which can change over time.  Please visit their website to see the current offers.  Frequent offer classes include: Single Ride, Monthly Membership, Annual Membership, Bike Share for All, Access Pass, and Corporate Membership.

- Through this project, you will answer these questions: 
  * What are the 5 most popular trips that you would call "commuter trips"? 
  * What are your recommendations for offers (justify based on your findings)?

Please note that there are no exact answers to the above questions, just like in the proverbial real world.  This is not a simple exercise where each question above will have a simple SQL query. It is an exercise in analytics over inexact and dirty data. You won't find a column in a table labeled "commuter trip".  You will need to analyze the data to determine your own definition of a communter trip and then write SQL queries to find the communter trips. You will find you will need to do quite a bit of data exploration using SQL to help you come up with your definition of commuter trip. In data exploration process, you will find a lot of dirty data, that you will need to either clean or filter out.

You can make any recommendations regarding the offers, including, but not limited to: market offers differently to generate more revenue, remove offers that are not working, modify exising offers to generate more revenue, create new offers for hidden business opportunities you have found, etc. 

#### All Work MUST be done in the Google Cloud Platform

One of the major objectives of W205 is for students to learn how to work in the cloud.  It's one of the biggest requests we get from employers who court our MIDS students.  In most businesses today, it's virtually impossible to justify doing anything in house anymore from a cost / benefit analysis.  Even when work is done in house, it's usually an in house cloud with a very similar architecture to the commercial clouds.

In the past, students have tried to do the work outside of the GCP, using their desktop or other environments.  Please don't so this.  For one reason, it's cheating, which can subject a student to academic misconduct charges.  Another reason is that this project is a great way to pick up some cloud skills, much needed in industry.

#### The Majority of Work must be done using BigQuery SQL

One of the major objectives of this project is to gain skills executing SQL against a big data scale-out SQL platform, such as Google BigQuery.  You will find BigQuery SQL similar to conventional SQL platforms (Oracle, mySQL, SQLite, MS SQL Server, etc.), but also you will experience some frustrations only found in big data SQL which will be a great learning experience.

You should primarily use BigQuery SQL.  You can make intermediate temporary tables (or view) in your own dataset in BigQuery as you like.  These make data exploration much easier.  It's much easier when you have made a temporary table with only clean data, filtered rows, filtered columns, new columns, summary data, etc.  

The results of your BigQuery SQL will be read into Pandas, where you will use the skills you learned in the Python class to print formatted Pandas tables, simple data visualizations using Seaborn / Matplotlib, etc.  

You can use Pandas for simple transformations, but remember the bulk of work should be done using Google BigQuery.

In the past, some students have tried to pull down the entire dataset into Pandas or even into another SQL database.  Please do not do this, as before it's cheating, and you are not picking up SQL skills against a big data scale-out SQL platform.

#### GitHub Procedures

In your Python class you used GitHub, with a single repo for all assignments, where you committed without doing a pull request.  In this class, we will try to mimic the real world more closely, so our procedures will be enhanced. 

Each project, including this one, will have it's own repo.  Using the git command line: clone the repo down into your cloud virtual machine; leave the master branch untouched; create a branch called "assignment"; only make changes to the assignment branch; stage, commit, and push changes frequently so as to not lose any work;  NEVER merge the branch!  Once you are finished: create 1 and only 1 pull request comparing the assignment branch to the master branch with your instructor as the reviewer.

If you decide to make more changes after you have created a pull request, you can simply close the pull request (without merge!), make more changes, stage, commit, push, and create a final pull request when you are done.

#### We have broken it down into 3 parts, about 1 weeks work each to help you stay on track, however, you will only turn in the project once time at the end or part 3!

## Part 1 - Querying Data with BigQuery

### What is Google Cloud?
- Read: https://cloud.google.com/docs/overview/

### Get Going

- Go to https://cloud.google.com/bigquery/
- Click on "Try it Free"
- It asks for credit card, but you get $300 free and it does not autorenew after the $300 credit is used, so go ahead (OR CHANGE THIS IF SOME SORT OF OTHER ACCESS INFO)
- Now you will see the console screen. This is where you can manage everything for GCP
- Go to the menus on the left and scroll down to BigQuery
- Now go to https://cloud.google.com/bigquery/public-data/bay-bike-share 
- Scroll down to "Go to Bay Area Bike Share Trips Dataset" (This will open a BQ working page.)


### Some initial queries
Paste your SQL query and answer the question in a sentence.

- What's the size of this dataset? (i.e., how many trips)

- What is the earliest start time and latest end time for a trip?

- How many bikes are there?


### Bonus activity queries

The bike share database offers multiple tables that can be joined to learn more interesting facts about the bike share business across all regions. These advanced queries are designed to challenge you to explore the other tables, using only the available metadata to create views that give you a broader understanding of the overall volumes across the regions(each region has multiple stations)

- Top 25 popular station pairs in each region

- Top 3 most popular regions(stations belong within 1 region)

- Total trips for each short station name in each region

- What are the top 10 used bikes in each of the top 3 region. these bikes could be in need of more frequent maintenance.



### Questions of your own
- Make up 3 questions and answer them using the Bay Area Bike Share Trips Data.
- Use the SQL tutorial (https://www.w3schools.com/sql/default.asp) to help you with mechanics.

- Question 1: 
  * Answer:
  * SQL query:

- Question 2:
  * Answer:
  * SQL query:

- Question 3:
  * Answer:
  * SQL query:



---

## Part 2 - Querying data from the BigQuery CLI - set up 

### What is Google Cloud SDK?
- Read: https://cloud.google.com/sdk/docs/overview

- If you want to go further, https://cloud.google.com/sdk/docs/concepts has
  lots of good stuff.

### Get Going

- Install Google Cloud SDK: https://cloud.google.com/sdk/docs/

- Try BQ from the command line:

  * General query structure

    ```
    bq query --use_legacy_sql=false '
        SELECT count(*)
        FROM
           `bigquery-public-data.san_francisco.bikeshare_trips`'
    ```

### Queries

1. Rerun last week's queries using bq command line tool (Paste your bq
   queries):

- What's the size of this dataset? (i.e., how many trips)

- What is the earliest start time and latest end time for a trip?

- How many bikes are there?

2. New Query (Paste your SQL query and answer the question in a sentence):

- How many trips are in the morning vs in the afternoon?


### Project Questions
Identify the main questions you'll need to answer to make recommendations (list
below, add as many questions as you need).

- Question 1: 

- Question 2: 

- Question 3: 

- ...

- Question n: 

### Answers

Answer at least 4 of the questions you identified above You can use either
BigQuery or the bq command line tool.  Paste your questions, queries and
answers below.

- Question 1: 
  * Answer:
  * SQL query:

- Question 2:
  * Answer:
  * SQL query:

- Question 3:
  * Answer:
  * SQL query:

- ...

- Question n:
  * Answer:
  * SQL query:


---

## Part 3 - Employ notebooks to synthesize query project results

### Get Going

Use JupyterHub on your midsw205 cloud instance to create a new python3 notebook. 


#### Run queries in the notebook 

```
! bq query --use_legacy_sql=FALSE '<your-query-here>'
```

- NOTE: 
- Queries that return over 16K rows will not run this way, 
- Run groupbys etc in the bq web interface and save that as a table in BQ. 
- Query those tables the same way as in `example.ipynb`


#### Report
- Short description of findings and recommendations 
- Add data visualizations to support recommendations 

### Resource: see example .ipynb file 

[Example Notebook](example.ipynb)
