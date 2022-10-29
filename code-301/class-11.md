# SQL vs. NoSQL

## Why this topic matters

This topic is important as learning how to store data efficiently to use with our applications becomes more of a concern. While both may be adequate solutions for smaller projects, knowing the advantages and disadvantages of SQL vs. NoSQL servers will help us in industry as well.

## SQL vs NoSQL Database Differences Explained with few Example DB

Based on [this article](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/?utm_source=tuicool).

1. Fill in the chart below with five differences between SQL and NoSQL databases.

   |                     SQL                     |                                   NoSQL                                    |
   | :-----------------------------------------: | :------------------------------------------------------------------------: |
   |         Relational database (RDBMS)         |                   Non-relational / distribution database                   |
   |                 Table-based                 | Document-based w/ key-value pairs or graph databases or wide-column stores |
   |             Pre-defined schema              |                               Dynamic schema                               |
   |             Vertically scalable             |                           Horizontally scalable                            |
   | SQL for  definining / manipulating the data |         UnQL for querying documents; varies from system to system          |

2. What kind of data is a good fit for an SQL database?

    Tabular data and smaller data are better fits SQL databases.

3. Give a real world example.

    A good example of tabular data is storing customer information since we'd always need to collect data like Name, E-Mail, Phone Number, Address, etc.

4. What kind of data is a good fit a NoSQL database?

    Hierarchical data and large data are good fits for NoSQL databases.

5. Give a real world example.

    A good example of hierarchical data is clothing since it can be split into Men's and Woman's, and then by clothing type such as Tops and Bottoms, etc.

6. Which type of database is best for hierarchical data storage?

    NOSQL databases are best for hierarchical data storage because of its key-value style of storing data (like JSON).

7. Which type of database is best for scalability?

    For vertical scalability-- increasing the power of the server via CPU, RAM, SSD, etc., an SQL database would be better.

    For horizontal scalabiilty-- adding additional servers to support the load, a NoSQL database is better.

    The difference between the two as summarized in this [Mission Cloud article](<https://www.missioncloud.com/blog/horizontal-vs-vertical-scaling-which-is-right-for-your-app#:~:text=With%20vertical%20scaling%20(%E2%80%9Cscaling%20up,memory%20workload%20across%20multiple%20devices>).

     is that vertical scalability is like trading in a Toyota for a Ferrari. It's faster but it can get extremely expensive and you're still limited to one car. Horiziontal scaling is like getting multiple Toyotas to add to a fleet. One alone might not be great, but having multiple can give us the power we need to get what we want done.

## SQL vs NoSQL or MySQL vs MongoDB

Based on [this video](https://www.youtube.com/watch?v=ZS_kXvOeQ5Y).

1. What does SQL stand for?

    It stands for **S**trucured **Q**uery **L**anguage.
 
2. What is a relational database?

    A relational database is a type of database that relies on knowing the structure or relationships between its data using schema.

3. What type of structure does a relational database work with?

    A relational database works with tables to store its data.

4. What is a ‘schema’?

    A schema tells us what data is allowed in our table. This is defined by using fields such as 'Name', 'Age', 'E-Mail', etc. and every record (row) needs to have a value for each field and *cannot* have any additional data (i.e. an extra field).

5. What is a NoSQL database?

    A NoSQL database is a type of database that doesn't rely on relational tables like a relational database.

6. How does it work?

    It works by creating collections which hold documents that look similar to JSON objects. The documents also do not have to follow the same schema-- they can have different data. Instead of holding data separately in various tables and `JOIN`ing them with queries, NoSQL databases also just store all of the info in one location per use. For example, they may have a Users and Post collection, and both would contain info such 'Username' 'E-Mail', etc. instead of using relations to get the data.

7. What is inside of a MongoDB database?

    MongoDB databases store collections which hold documents. For example it can store a collection for 'Users' and 'Posts' and have documents that look like `{ 'username' : 'kennywlino' , 'email': 'kennywlino@gmail.com'}` and `{'post' : '' , 'date' : '2022-10-29'}`.

8. Which is more flexible - SQL or MongoDB? and why.

    MongoDB is more flexible because it doesn't have to adhere to any sort of schema. That means we can add data however we want without restructuring the database.

9. What is the disadvantage of a NoSQL database?

    One of the disadvantages of a NoSQL database is that we're more prone to having duplicate data. If we have related data (e.g. like the "Orders", "Users", and "Products" mentioned in the video) that means we would also have to update each of them separately.

## Things I want to know more about
