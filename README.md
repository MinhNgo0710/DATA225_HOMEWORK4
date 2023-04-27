           DATA-225- DB SYSTEMS FOR ANALYTICS ASSIGNMENT


MEMBERS: PRIYANKA AKULA, SOMNA SATTOOR, SOWJANYA PAMULAPATI, SHREYA CHIKATMARLA, MINH NGO


Abstract :

In this homework, we will setup docker with MongoDB image, and also a free cluster on mongodb. From there, we load this free cluster with test database from Atlas. We will then connect to this cloud cluster from a local mongo compass as a database management software. We will perform common CRUD operations, and some analytical queries using mongodb’s aggregation pipeline.

On the other hand, we also connect to this cloud cluster of mongodb using mongodb python connector and Jupyter Notebook. We will then analyze the data that we get in the test database by doing interpretation of nosql data into relational data model concept. At the end, we will visualize the aggregated data in Jupyter Notebook using python and industry standard visualization libraries. 

In this homework, we are using Neo4j, a graph database, to analyze the titanic dataset and get insights into the relationships between passengers, their demographics, and their odds of survival. The dataset is visualized as a graph using Neo4j, and significant information is retrieved using CRUD operations and analytical queries from the graph using Cypher, Neo4j's query language.


Motivation :

Mongodb and other nosql databases are extremely popular recently in the industry. We would like to use this opportunity to get some decent exposure to the world of mongodb collection and aggregation. We also want to explore the situation where we want to build some bridges between traditional relational modeling approach and nosql. This will enable us to be able to see both the pros and cons from both side of the technologies. 
Visualization and data analyzation are also important as they are what matter to stakeholders in any organizations. This gives us the motivation to use Jupyter Notebook to visualize our aggregated data.

Popular graph database Neo4j was created primarily to store and manage knowledge graphs. Due to its characteristics, it is the perfect tool for creating intricate data models that are challenging to express using conventional databases. The objective of this project is to demonstrate Neo4j's potential and capabilities, such as graph traversal and algorithms, and show how it can be used to construct a knowledge graph to uncover new information and guide decision-making.


Blog :

We document this project on the following repository with a detailed Readme page:
https://github.com/MinhNgo0710/DATA225_HOMEWORK4

Dataset:  https://1drv.ms/x/s!Anrxb421tNmH5yu7dPUZCt7RyLWv?e=4nMeez

Key learning :

•	Being able to setup a free cloud cluster of mongodb
•	Being able to connect to the cloud mongodb from various tools
•	Being able to use mongo compass and Jupyter notebook
•	Learning how to use aggregation and pipelining in mongodb
•	Learning how to perform CRUDs on mongodb’s document/collections
•	Learning how to use filtering to query for data in mongodb
•	Being able to process mongodb data in Python with Python Pandas library
•	Learning how to use Python Mathplotlib to visualize data in graphs
•	Learning how to use Python to process nosql data and json expansion
•	How to display data as a graph in Neo4j 
•	How to query the graph and extract useful information with Cypher, Neo4j's query language.
•	How to identify relationships between data points that may not be apparent in a standard tabular format.
•	How to Use a Graph Database to Understand a Dataset. 


Project Workflow

Technical difficulties
-	Most of team members are not too familiar with nosql on a day-to-day workflow
-	This project is also our first time doing many devops setup that is usually handled by a specific devops or infrastructure team, not by the application developer or data science team
-	The amount of work is tremendous and daunting as there is no firm limit into what we are supposed to do.
-	Setting up connection to mongodb neo4j taking some times to troubleshoot and debug
-	Team members having different levels of setup requiring different levels of packages installation.
-	Performance issues: As the size of a Neo4j graph grows, users may experience performance issues such as slow query times, increased memory usage, or even crashes. These issues can be caused by a variety of factors, such as inefficient query design, suboptimal indexing, or inadequate hardware resources.
-	Data management issues: Users may face difficulties managing their data in Neo4j, such as importing or exporting data, modifying schema or constraints, or performing backups and restores.
-	Query language issues: Users may experience difficulties with the Cypher query language used in Neo4j, such as incorrect syntax, inefficient query design, or limitations of the language itself.
-	Integration issues: Users may face difficulties integrating Neo4j with other technologies or systems, such as web frameworks, messaging systems, or NoSQL databases.
Innovation :

MongoDB is a popular NoSQL document database that is used to store and manage semi-structured data. There are several ways in which you can innovate using MongoDB:

Flexible data modeling: One of the key advantages of MongoDB is its flexible data modeling capabilities. You can store data in a variety of formats, including JSON, BSON, and CSV, and you can easily change your data model as your needs evolve. This flexibility can be particularly useful for applications that need to store data that doesn't fit into a traditional relational database schema.

Distributed data processing: MongoDB is designed to be distributed, which means you can scale your database horizontally across multiple servers. This can help you to handle large volumes of data and ensure high availability and fault tolerance.

Advanced querying: MongoDB provides a powerful query language that allows you to query your data in a variety of ways. You can use complex queries, such as aggregation pipelines, to perform advanced data processing tasks and extract meaningful insights from your data.

Real-time analytics: MongoDB can be integrated with various analytics tools, such as Apache Spark and Hadoop, to perform real-time analytics on your data. This can help you to identify trends and patterns in your data and make data-driven decisions in real-time.

Machine learning: MongoDB can also be used in conjunction with machine learning algorithms to build intelligent applications that can make predictions and automate decision-making processes. By combining the flexibility of MongoDB's data modeling capabilities with the power of machine learning, you can create applications that can learn and adapt to changing conditions.

Overall, there are many innovative ways to use MongoDB, and the above suggestions are just a few examples. The key is to think creatively about how you can leverage the power of NoSQL databases to gain new insights into your data and build intelligent applications.

Neo4j is a powerful graph database management system that is used to store, query, and analyze highly connected data. There are several ways in which you can innovate using Neo4j:

Graph-based data modeling: One of the most innovative things you can do with Neo4j is to design your data model in a graph-based manner. This approach involves identifying entities and their relationships and then creating nodes and edges to represent them. By doing so, you can uncover previously hidden insights and relationships within your data.

Graph algorithms: Neo4j provides a rich set of graph algorithms that can be used to analyze your data. These algorithms can help you identify patterns, clusters, and other useful information within your graph.

Real-time graph processing: Neo4j allows for real-time processing of graph data, which means you can build applications that can make decisions based on the current state of your data. This can be especially useful for applications that require fast responses, such as fraud detection or recommendation systems.

Graph visualization: Neo4j also provides tools for graph visualization, which can help you to better understand the structure of your data. You can use these tools to create interactive visualizations that allow you to explore your graph and discover new insights.

Overall, there are many innovative ways to use Neo4j, and the above suggestions are just a few examples. The key is to think creatively about how you can leverage the power of graph databases to gain new insights into your data.


 
I.	Architecture setup & Tool

A.	We set up a local MongoDB using docker and MongoDB image.

We proceed by installing and set up docker desktop, MongoDB image. After pulling the MongoDB, we continue to execute the mongo image and start setting up the test database.
As detailed in the images below, mongo image is up and running on default port 27017/tcp. 
B.	Cloud Cluster of MongoDB

To make this database available to all of us over the Internet, we set up a free cluster on Mongodb cloud with the image in part A. This free cluster/shard is then loaded with test databases as provided from Atlas. We connect to this via Mongo Compass.

This cloud cluster can be accessible via this connection string: mongodb+srv://doremon0710:M010980398@cluster0.1w74fo2.mongodb.net/test

Tools: Mongo Compass, Jupyter Notebook for code/visualization

 
II.	Problem and solution 

Approach :

We selected this sample database from MongoDB: 

https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/.

From this sample dataset, we establish a connection from Jupyter Notebook to the cloud cluster that we setup in part I. above using Mongo Python connector/driver. We will then analyze and visualize the data using popular Python Pandas Dataframe library. The Jupyter Notebook file is included along with the submission.

















In this part, we query the https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/#sample_restaurants.neighborhoods collection.




















We can see that the geometry column contains nested json, we will need to expand this column to use the information within this column.






















After this, we have the complete neighborhood collection/table that is ready to use for analyzation and visualization.

Data analyzation and visualization :

We use default python default plot package to visualize
On another hand, we can also visualize the top 10 areas with the least amount of restaurants. They all have only 1 restaurant per each area as what we can see.
We can also perform basic descriptive analysis on this dataset. Python will automatically 
select any numerical column to do so. It gets us the total count, mean, std, min, 25% percentile and more.
 
In this part, we query the https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/#sample_restaurants.restaurants collection.

Just like the above part, we see that the address column contains nested json. So, we will also expand this into corresponding fields to have a more complete view.
We also see that the grade column consists of a series of grade per each row. To better evaluate the grade, we only care about the most recent grade. To do so, we will design a custom function to get only the recent grade per each restaurants.
 
Now, we can visualize this table:

We see that most restaurants in this collection have grade A as most recently grade.

Visualize the location distribution of the restaurants :

A majority of restaurants is located in North America.




















How about the locations of only grade A restaurants?

As we see, even if we only care about grade A restaurants, it is almost the same as the above visualization. This suggests that the sample dataset only has North America data.
 

















	
III.	CRUD in MongoDB compass

We will also use the sample_restaurants.neighborhoods as target collection for this part.
First, we search (find) for a neighborhood called “Bedford”
Then, we create a new neighborhood with some random information as the below:

 
We create this new “row” with the below information:
geometry: Object
coordinates: Not Available
type: "Polygon"
name: "HillView"

After the new row is created, we simply search for this with the name:
 “Hillview” to verify that we create it successfully:
We can see that the total of documents is now 196 from 195, and we also see the new document in the search result.

Now, we modify the document. 
 
The Hillview document has been modified as what we see here.

Now, we will finally do deletion/remove of the newly created document.
 
After the deletion, the total count of document is back to 195, and we no longer find the Hillview document.

IV.	Analytical queries with MongoDB compass

We use aggregation to perform this task on the restaurant collection. 

A.	For example, we wish to group by the restaurant by cuisine and count how many of the restaurant per each group. In SQL, we simply do something such as “select… group by…”. We do the same thing in MongoDB but with MongoDB’s aggregation as the below:

/**
 * _id: The id of the group.
 * fieldN: The first field name.
 */
{
  _id: "$cuisine",
  cuisine: {
    $first: "$cuisine"
  },
  count: {$sum: 1}
}




We see that the aggregation per group of cuisine has been done, with the total count per each group is included in the results. Chicken cuisine group has 410 restaurants.

We then do another sorting aggregation on top of the previous group by to see the top cuisine group with the greatest number of participating restaurants:
/**
 * Provide any number of field/order pairs.
 */
{
  count: -1
}
 
Now, we know that most of the restaurants in this collection are offering American cuisine, and up to 6183 of them. The next popular one is Chinese cuisine with 2418 restaurants.

B.	 Now, we would like to write an analytical query to calculate the average score/grade for each restaurant over some period. (As what we see, in the collection, each restaurant has a series of grades)

We run the below aggregation pipeline:
[
  {
    $unwind: "$grades",
  },
  {
    $group: {
      _id: "$name",
      average_grade: {
        $avg: "$grades.score",
      },
    },
  },]
Now we have the average score per each restaurant.
We can also sort the result too. 





















NEO4J

Installed Neo4j:


 


















Importing the CSV file:

 

 





Creating Nodes and relationships:

 
 
 
 
 
 
 
 
        



Entire Representation of graphs:

 
List of passengers who travel along with spouse and are in 1st class and survived:

 

List of passengers who travel along with Children and are in 1st class and survived:

 




List of passengers who travel along with children and are in 3rd class and not survived:

 



Count of Passengers whose last name is same:

 
List of passengers who share cabin with each other:

 

Updating pclass to 2 where passenger name is ‘Heikkinen, Miss. Laina’

 






Deleting the node and its relationships, whose passenger name is “Cumings, Mr. John Bradley”

 






Visualizations:

 
     



Comparing MongoDB, Neo4j:

•	Neo4J allows for tree-based navigation over graphs, unlike MongoDB does not support graph representation of document storage.
•	The query language used by MongoDB, termed MongoDB Query Language (MQL) is comparable to SQL. On the other hand, Neo4j makes use of the Cypher query language, which was created especially for using graph data.
•	The data in MongoDB is stored in flexible, semi-structured BSON documents and is a document-based NoSQL database. Data in Neo4j is described as nodes, relationships, and characteristics in a graph-based NoSQL database.
•	SQL is not supported in Neo4j. MongoDB supports read-only SQL queries with the MongoDB Connector for BI.
•	In most situations, MongoDB surpasses Neo4j on performance, however in rare cases, Neo4j outperforms MongoDB.
•	MongoDB provides a scalable and adaptive solution for businesses that need to store and manage huge amounts of data. For Neo4j the method is robust and performant, but we believe it is better suited to a wide range of situations that are either too expensive or too rigid to address with a relational database.
•	MongoDB is a flexible and adaptable solution that needs to store and handle massive amounts of data. The technique is strong and performant for Neo4j, but we feel it is better suited to a wide range of circumstances where a relational database is either too expensive or too rigid to solve. Upgrading between Neo4j versions is difficult since we must upgrade step by step through the cycle; you can only jump several versions with the business license.

Use of NOSQL databases other than MongoDB and Neo4j:

DynamoDB

 


The above picture shows the console of the aws services DynamoDB where S3, Lambda and DynamoDB are used.

 


S3 is an abbreviation for Simple Storage Service, a fully managed cloud storage service offered by Amazon Web Services (AWS). It is designed to store and retrieve any quantity of data from anywhere on the internet and it offers a highly scalable and long-lasting storage architecture.

Basically, S3 is a bucket and our dataset ctr.csv is stored as a bucket in S3.


 

   

Lambda is a serverless computing tool that enables developers to run code without the need for server or infrastructure management. Developers can upload their code as a function to Lambda, and AWS will handle the underlying hardware and scaling. After storing the file in the S3 bucket, next comes the Lambda. Here, we have imported the csv file and had run the code and exported the JSON.


   This is the Test code.
 
        

 

 

       

DynamoDB is a fully managed NoSQL database service. It is intended to provide highly accessible and scalable database storage for web, mobile, gaming and other applications. It is a key-value and document database that enables developers to save and retrieve data with a single API call. 

It offers automatic scaling, which means that when the amount of data stored in the database grows, DynamoDB's throughput capacity can automatically expand to handle the growing strain.

 

 

The DynamoDB PartiQL editor is a tool that allows users to write and execute PartiQL queries straight from the DynamoDB console. This editor provides an easy-to-use interface for querying DynamoDB data without requiring developers to write complex code.
We have used SELECT Query to display at the records of the titanic dataset.















