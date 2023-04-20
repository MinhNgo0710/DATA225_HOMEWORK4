## HOMEWORK4

## **Abstract**

In this homework, we will setup docker with mongodb image, and also a free cluster on mongodb. From there, we load this free cluster with test database from Atlas. We will then connect to this cloud cluster from a local mongo compass as a database management software. We will perform common CRUD operations, and some analytical queries using mongodb’s aggregation pipeline. \
On the other hand, we also connect to this cloud cluster of mongodb using mongodb python connector and Jupyter Notebook. We will then analyze the data that we get in the test database by doing interpretation of nosql data into relational data model concept. At the end, we will visualize the aggregated data in Jupyter Notebook using python and industry standard visualization libraries.

## **Motivation**

Mongodb and other nosql databases are extremely popular recently in the industry. We would like to use this opportunity to get some decent exposure to the world of mongodb collection and aggregation. We also want to explore the situation where we want to build some bridges between traditional relational modeling approach and nosql. This will enable us to be able to see both the pros and cons from both side of the technologies. \
Visualization and data analyzation are also important as they are what matter to stakeholders in any organizations. This gives us the motivation to use Jupyter Notebook to visualize our aggregated data.

## **Blog**
 We document this project on the following repository with a detailed Readme page:

## **Key learning**

- Being able to setup a free cloud cluster of mongodb
- Being able to connect to the cloud mongodb from various tools
- Being able to use mongo compass and Jupyter notebook
- Learning how to use aggregation and pipelining in mongodb
- Learning how to perform CRUDs on mongodb’s document/collections
- Learning how to use filtering to query for data in mongodb
- Being able to process mongodb data in Python with Python Pandas library
- Learning how to use Python Mathplotlib to visualize data in graphs
- Learning how to use Python to process nosql data and json expansion

## **I.	Architecture setup & Tool**
### **A. We setup a local mongodb using docker and mongodb image.**
We proceed by installing and setup docker desktop, mongodb image. After pulling the mongodb, we continue to execute the mongo image and start setting up the test database. \
As detailed in the images below, mongo image is up and running on default port 27017/tcp. 
![Docker setup and mongo image container download](/images/pull_mongoimage.jpg)

![Docker setup and mongo image container download](/images/docker_running.png)

### **B. Cloud Cluster of mongodb**
To make this database available to all of us over the Internet, we set up a free cluster on Mongodb cloud with the image in part A. This free cluster/shard is then loaded with test databases as provided from Atlas. We connect to this via Mongo Compass.

This cloud cluster can be accessible via this connection string: mongodb+srv://doremon0710:password@cluster0.1w74fo2.mongodb.net/test

Tools: Mongo Compass, Jupyter Notebook for code/visualization
![Mongodb Cloud Cluster](/images/cloud_mongodb.png)
This cloud cluster is a free instance/shard setup using mongocloud service.
![Mongodb Cloud Cluster](/images/database_loading.png)
We then load all of test database. They are on the left hand-side of the mongo compass UI.

## **II. Problems and solutions**
### **A. Approach**
We selected this sample database from mongodb: https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/. From this sample dataset, we establish a connection from Jupyter Notebook to the cloud cluster that we setup in part I. above using Mongo Python connector/driver. We will then analyze and visualize the data using popular Python Pandas Dataframe library. The Jupyter Notebook file is included along with the submission.

![Mongodb Connector](/images/jupyter_mongodbconnector.png)
We installed mongodb driver/connector and then connected to mongodb cloud cluster.

In this part, we query the https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/#sample_restaurants.neighborhoods collection.
![Neighborhood](/images/neighborhoods.png)
We do a "select all" query to the neighborhood dataset.

We can see that the geometry column contains nested json, we will need to expand this column to use the information within this column.
![Expansion of nested json](/images/expan_nested_json.png)

We then expand the nested json column to get useful information. We do so by creating a custom function
![Custom function one](/images/custom_function.png)

After this, we have the complete neighborhood collection/table that is ready to use for analyzation and visualization.

#### **Data analyzation and visualization**
We use default python default plot package to visualize.
![graph1](/images/graph1.png)

On another hand, we can also visualize the top 10 areas with the least amount of restaurants. They all have only 1 restaurant per each area as what we can see.
![graph2](/images/graph2.png)
We can also perform basic descriptive analysis on this dataset. Python will automatically select any numerical column to do so.
It gets us the total count, mean, std, min, 25% percentile and more.

![descriptive_stat](/images/descriptive_stat.png)

---
In this part, we query the https://www.mongodb.com/docs/atlas/sample-data/sample-restaurants/#sample_restaurants.restaurants collection.
![restaurant](/images/restaurant.png)

Just like the above part, we see that the address column contains nested json. So, we will also expand this into corresponding fields to have a more complete view.
![expan_nested_json2](/images/expan_nested_json2.png)

We also see that the grade column consists of a series of grade per each row. To better evaluate the grade, we only care about the most recent grade. To do so, we will design a custom function to get only the recent grade per each restaurants.
![custom_function2](/images/custom_function2.png)

Now, we can visualize this table:
![graph3](/images/graph3.png)
We see that most restaurants in this collection have grade A as most recently grade.

#### **Visualize the location distribution of the restaurants**
A majority of restaurants is located in North America.
![graph4](/images/graph4.png)
### **How about the locations of only grade A restaurants?**
As we see, even if we only care about grade A restaurants, it is almost the same as the above visualization. This suggests that the sample dataset only has North America data.
![graph5](/images/graph5.png)

## **III. CRUD in mongodb compass**
We will also use the sample_restaurants.neighborhoods as target collection for this part.
First, we search (find) for a neighborhood called “Bedford”
![neighborhood_filter](/images/neighborhood_filter.png)

Then, we create a new neighborhood with some random information as the below:
![mongodb_insert](/images/mongodb_insert.png)

We create this new “row” with the below information: \
geometry: Object \
coordinates: Not Available \
type: "Polygon" \
name: "HillView" 

After the new row is created, we simply search for this with the name: “Hillview” to verify that we create it successfully:
![search](/images/search.png)
**We can see that the total of documents is now 196 from 195, and we also see the new document in the search result.**

Now, we modify the document. 
![edit_document](/images/edit_document.png)
![mongodb_modify](/images/mongodb_modify.png)
The Hillview document has been modified as what we see here.

Now, we will finally do deletion/remove of the newly created document.
![prepare_deletion](/images/prepare_deletion.png)

After the deletion, the total count of document is back to 195, and we no longer find the Hillview document.
![search2_noresult](/images/search2_noresult.png)

## **IV. Analytical queries with mongodb compass**
We use aggregation to perform this task on the restaurant collection. 
### **A.**

For example, we wish to group by the restaurant by cuisine and count how many of the restaurant per each group.
In sql, we simply do something such as “select… group by…”. We do the same thing in mongodb but with mongodb’s aggregation as the below:

```python
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
```
![group1](/images/group1.png)
We see that, the aggregation per group of cuisine has been done, with the total count per each group is included in the results. Chicken cuisine group has 410 restaurants.

We then do another sorting aggregation on top of the previous group by to see the top cuisine group with the greatest number of participating restaurants:

```python
/**
 * Provide any number of field/order pairs.
 */
{
  count: -1
}
```

![sort2](/images/sort2.png)
Now, we know that most of the restaurants in this collection are offering American cuisine, and up to 6183 of them. The next popular one is Chinese cuisine with 2418 restaurants.

### **B.**
Now, we would like to write an analytical query to calculate the average score/grade for each restaurant over some period. (As what we see, in the collection, each restaurant has a series of grades)

We run the below aggregation pipeline:
```
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
```
![unwind](/images/unwind.png)
Now we have the average score per each restaurant.
We can also sort the result too. 
![sort3](/images/sort3.png)
