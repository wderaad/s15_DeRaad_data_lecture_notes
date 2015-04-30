# Data Engineering Lecture Notes 

# Spring 2015

***
## Lecture 1

### Associated with Big Data

* Social Networking
* Data Analytics
* Sampling
  * Revamping and changing in statistics
  * With all of the information you can give exact answers
  * Machine learning at a lower level
* Storage
  * NoSQL not great for arbitrary queries after the fact. Easy to add and remove structures (schemes). 
  * SQL is great for answering queries that you've optimized using table structures (schemes), but can also work for un-optomized queries. 
  * Data Modeling is hard
   * Data in the wrong model is hard to reformat and use
* Data Collection & Cleaning
  * Store in raw from then perform batch jobs
  * Store data using certain model
* InfoViz
  * D3
   * JavaScript that  will help you vizualize data in a browser

***
### Data Lifecycle

1. Question?
  * Curation "Which data sets should be collected"
  * Triage "Priortization of the data sets"
  * Persistance "How long the data will be around"
2. Collection
  * Generation
3. CleanUp
4. Storage
5. Processing/Analysis
6. Query
  * Vizualize 
  * Act

***
### Most common interaction with big data

* HTTP request  for a html page
  * Request Response Cycle

***
## Lecture 2

***
### Markdown Lecture

* Italics, Bold, Strikethrough
* List 
* Links
* Code Blocks
* Tables

***
### Web Request
* Web Browser -> Web Server -> Handler (Web server notifies url was accessed with specific method)
	* Get
	* Post
	* Delete
	* Put
* Script Tags - can point at another url
* Asking for index.html provides a service
* Nav Bars, Search bars, Various structures are all modularized. 
	* Services accept and return JSON or xml

***
### Restful
Representation State Transfer
* Resources all over the world referenced by a url/uri(more general) and that resource will be passed to you in some format
	* CRUD operations on url Create, Read, Update, Destroy

***
#### Service
* On any service /users/{id}
	* Get - used to read current state of a user/resource
	* Post - create a new user/resource 
		* Data passed that helps create a new user
	* Put - Update an existing user/resource
	* Delete - Destroy user or resource
	
***
### Review Ruby example
	* Sinatra used for prototype not production
	
***
## Lecture 3

### Restful Web Services

***
 Operations on a single resource

* REST is an architectural style for web services
	* An approach to developing web services that mimics the design of the Web itself
	* Your services provides access to a linked set of resources
	* For each resource you can perform services similar to HTTP operations. (See previous lecture for operations)
* Examples
	* GET /api/1.0/users
		* 1.0 is the version number, great for deploying new versions without conflict
		* Retrieve a list of all users.
	* GET /api/1.0/users/0
		* Retrieve the details of User 0.
	* POST /api/1.0/users
		* Create a new user
	* PUT ../users/0
		* Update User 0.
	* DELETE ../users/0
		* Delete User 0.
	* GET ../search?q=tattersail
		* Perform a search with the query tattersall.
* Each operation may produce a result
	* With RESTful services, JSON format is king
* POST and PUT methods typically send data
	* JSON Format
	* In URL or body of HTTP request
		* GET-data may appear as query params
	* HTML and XML also possible
	* Authentication data appears in HTTP headers

***
Operations on two/multiple resources

* Nested Approach
	* GET ../posts/0/comments/1
		* Get the first comment on post 0.
	* POST ../posts/0/comments
		* Create a new comment on post 0.
* Alternate approach 
	* While performing an operation on one resource, you referernce another resource
* Issues
	* Security: How do you authenticate users?
	* Identity: How are ids assigned to resources?
	* Failure: How do we handle failure situations?
		* In the example today, handled in JSON
		* HTTP status codes could have been used i.e. 404
		* Most series will us a combination of both
	* Persistence: How are resources stored?

### Example

* Contacts Web Service
* Implemented in both Ruby and Javascript
* Technology Used
	* Sinatra
	* Rspec
	* Typhoeus
	* Node
	* Express

* Web Service about contacts
	* Details stored in the model object
		* Search a contact
		* Query birthday 
		* Query upcoming birthdays
		* Summary response/full response using a hash table that is created on the fly
	* Client Side
		* Handle Request 
			* Handle error responses
			* Reference a url, http request, and possible data
	* Client Side Test
		* Rspec should explain what went wrong in natural language
			* i.e. “should list available contacts”
		* Reset each test after completion
			* Each test should be independent of one another. 
	* Server Side Test
		* Independent of clients and network connections is our server correct.
		
***
## Lecture 4

### Git Version Control

“Mastering Git”

### GitHub

#### Workflow

* Branch and merging is preferred over rebasing
* Pull Request for adding a finished branch containing a new feature to the master branch (production)

### Web Service Challenge

``` 
http://epic-analytics.cs.colorado.edu:4000/
‘/api/1.0/methods’
```

### Contact Server JavaScript
Review Code Base

***
## Lecture 5

### NODE.JS
- Server side Javascript
- Most code in node is packaged inside of a module
- Listen connects the server to the port and local host
- console.log() - prints to standard out
“If there is no future work remaining node will shut down.”

### Event Loop
- Add processes to the event loop using the following:	
	- process.nextTick() “Execute on the next iteration of the event loop, prioritize over any IO related callbacks”
	- setImmediate() “Same as next tick but let IO callbacks process first”
	- setTimeout() “Takes a parameter that specifies how long to wait before the function is called, not guaranteed exact”
	- setInterval() “Takes a parameter that specifies how often the function be called (i.e. 1000 (ms) - 1 second intervals)”
- Can cause “callback hell”, which can be solved with closures. 

### Node Execution Model
- For user-written code, Node is single threaded!
- Any code that you write is guaranteed to be synchronous
- You do not have to worry about race conditions
- IO is handled in parallel
- If you issue an asynchronous call for IO - your callback is registered

***
## Lecture 6

### Express 
* Web Application framework written in Javascript for use in Node.js
* Its design was influenced by Sinata
* Express makes it easy to define the endpoint of your web-base service
* Minimal Framework. It is designed to be augmented with node packages using middleware
Example
#### Example
* Install expresss
* Install necessary middleware

***
## Lecture 7

### ANGULARJS
* Web Application that lives on the client-side 
* Written in Javascript	
* Provides an implementation of MVC
* Client side designed to live on top of JSON-base RESTful services

#### Core Concepts
* Data Bindings 
	* The value of an HTML tag can be associated with a model object, stored in the controller. Angular updates the other whenever one changes. 
* Controllers
	* Associated with a portion of your HTML page, defines all of the states and methods that can be accessed in that section of the page
	* Modularize your web app, and decompose data and functionality into small manageable tasks. 
* Services
	* Controllers are used to merge data for some portion of a page “while its being displayed”. Controllers come and go.
	* To maintain a state between controllers you can create a services
	* Services are created when Angular app is initialized and remains for the app life cycle
* Directives
	* Primary use is to allow Angular to integrate into HTML naturally
	* Can be used to create reusable components that combine controllers, data and HTML
		* i.e. you can create a login form components, that can be re-used across multiple objects
* Embeddable
	* Angular can control as much or as little of a web page
	* Easy to embed a small Angular component into an existing page
* Injectable
	* Dependency injection (Employee/Database Example)
	* Angular’s system locate dependencies at run-time and inject them into the component that needs them

#### Modules
* A module is the primary way to package up a set of controllers into an Angular app
* To create a module, git it a name and its its dependencies
``` angular.module(‘contactsApp’,[]) ```
This creates a module called contactsApp with dependencies []
* Once you have a module defined in Javascript, you can tell Angular where it lives in the html with the ng-app directive

#### Controllers
* You need a controller to do anything
* Controllers are declared using the controller function
``` angular.module(‘contactsApp’).controller(‘MainController’,[<dependencies and code.]) ```
* Controller example with two-way data binding

#### Directives
* ng-show : display an HTML element if a contition 
* ng-hide
* ng-repeat 

***
## Lecture 8

### Angular Example
* index.html
	* Javascript included in bottom of body
	* Bootstrap used for styling
* Angular app is on the client side
* Node app is on the server side
* When Angular is given a promise it waits till they all succeed until loading the page
* Promise library is called using $q 

***
## Lecture 9

### Javascript and Angular

View Javascript Readme.md explaining the use of the following:

```
var self = this;
self.data - “Interesting!”;
self.update = function(){
	self.data = “Even More Interesting!”;
}
```
* Reviews:
	* Implicit Bindings
	* Explicit Bindings

* IIFES
	* Follows the module pattern
	* **Javascript - ”Blocks do not create scope functions do!”**
``` 
(function( param ) {
	<function body>
} (actual));
``` 

### Getting data from twitter

* Reactivate twitter account
* Checkout twitter developer site
	* Bottom right > manage your apps

***
## Lecture 10

* Consumer keys, Access tokens
	* Access to Twitter’s APIs are secured by OAuth
		* OAuth is a Web-based service inceptions with users and applications
	* With Twitters a consumer key identifies a particular app/developer
	* Allows an application to act on behalf of many users
		* you might ship you app with its consumer keys but with no access tokens. 
		* Then when you launch the app, it allows the user to sign into your twitter account.
			* Twitter will then send an access token/secret for you application to store on behalf of the user. 
	* We circumvent the account long in step by creating access token on the developer app creation
* Install **rbenv** and **ruby-build**
* Review lecture notes to run get_tweets
* Twitter requires we sign every request with an Authorization header

***
## Lecture 11

### Class Hierarchy 

* Twitter Request
	* RateLimits
	* Max Id Request
		* Timeline
		* Search Api
	* Streaming Twitter Request
		* Filter Track Stream
		* Public Strema
	* Cursor Request
		* Friends Id
		* Follower Id

***

* Contracts are created using interfaces in statically-typed lungs such as java
* In dynamically-typed languages like ruby fail fast

### Param and Props

* Added Features
	* Ability to control if a parameter is included in a reduces 
	* Ability to display parameter that are being sent in a request

### Logging

* Logging helper is used to create a default logger
	* Created in TwitterRequest’s constructor
	* Accessed using the log attribute

### Rates

* Helper invokes a twitter endpoint to get the app’s current set of rate limits
	* Limits stored in a class variable to be shared across all TwitterRequest instances

### Requests

* MaxIdRequest
	* Subclass for endpoints that need to traverse timelines with max_id parameters
* CursorRequest
	* Similar to MaxId however it does not need to define a contract for subclasses
	* Can implement all required functionality directly

### Timeline

Loops until all tweets are accessed or 16 request are successful

### Search 

Loop until we see zero tweets returned 

### Streaming Twitter Request

* Collect method is designed to run forever
* Create event handlers on streaming request 
	* on_headers: Response has started to stream back to us
	* on_body: Some data has been received from the server to process	
	* on_complete: Response has finished, can be used to determine to close connection
* Client Side
	* Can call request shutdown method
### Homework 3 Available

***
## Lecture 12

Homework 3 now available

### Document Database

Resources: 

* “Big Data: Principles and best practices of scalable realtime data systems”
* “Making Sense of NoSQL: A guide for managers and the rest of us”

#### Scaling with Traditional Databases

Example:

* “Imagine you’ve been asked to build a system that keeps track of page views on particular URLS
* Figure: Traditional Table
* Leads to issues when your application gets popular
	* Solution add a queue between your web server and the database code
	* Not a true solution
		* Adding workers to paralyze the queue doesn’t work because the database is the bottleneck
* Solutions:
	* Vertical Scaling:
		* Short term solution:
			* New Equipment - High Cost
			* Implement Cache in-between database and server, only allow writes to database. All reads hit queue
	* Shard the database:
		* Multiple copies of the database
			* Create several instances of the database. (Most likely on separate machines
			* Partition data across those databases
				* Develop a partition strategy, perhaps MD5 hash some aspect of the input data and then mod that value by the number of shards. 
				* Write the data indicated shard
* Not great solution due to shard failure and added application complexity
	* Fault tolerance is hard
	* Complexity is pushed to the application layer

#### NoSQL

* NoSQL databases are ones which are aware of their distributed nature
	* The manage sharing and replication
	* They are horizontally scalable
		* If you need more disk space, add a server
		* If you need computation to go faster, add a server
* Avoid mutable data
	* If a value changes you write a new immutable copy of the updated data
* Fault tolerant

#### Types of NoSQL Databases

* Key-Value
	* Database Hash Table
	* Values are un-typed
	* Simple
* Graphs
	* Databases optimized to store graph structures
	* Provide structural query languages
	* Efficiently traverse graphs
	* Shortest path between nodes
* Columnar
	* Column Family Stores
	* Able to scale to enormous amounts of data
	* Able to achieve fast writes
		* While still maintaining reasonable read performance
	* Netflix uses Cassandra to store and serve movies 
	* Column families can think of as a table
		* Consists of rows that have unique row keys
			* Rows consist of columns
				* Columns consist of a key and a value pair
	* Essentially hash tables all the way down
	* Grouped Rows on disk
* Documents
	* Similar to key-value with a little more structure
	* You enter documents (a bag of key-value pairs)

**Why NoSQL?** 
There is no schema. 
There is nothing that says: in column 5 of table 2, you will find an int: in column 6, you’ll find a VARCHAR, etc. 
You are often free to store anything in one of these databases
* Examples:
	* Document Stores:	
		* Each document can have a different set of key value pairs (name, location, birthday), (pet, bird, age)
	* Columnar Store: each row in a columnar store can have different columns 

***
## Lecture 13

### CouchDB

* Document NoSQL Database
	* Stores documents
	* Each document contains everything that might be needed by an app
	* No schema is enforced: each document can have different attributes
		* Allows for natural modeling of domains
* Written in Erlang
	* Built in support for concurrency
	* Built in fault 
* Design braces the web
	* RESTful API
	* Built for Distribution
* CAP Theorem: **(Pick any two)**
	* **Consistency**: All clients see the same data even in the presence of concurrent updates
	* **Availability**: All clients are able to read or write the data store when they want
	* **Partition Tolerance**: A database can be split across multiple servers
* CouchDB chooses: **Availability and Partition Tolerance**

#### CouchDB Internal:

* B-Tree storage engine
	* Automatic sorting; Allows searches, insertions, and deletions to occur in ```O(lg)```
* Employs MapReduce over this B-Tree to compute views of the data; allows for parallel and incremental computation
* No Locking
* Validation: Validation functions can be written in JS for a particular class of documents
	* Safeguard against malicious data 
* Incremental Replication
* Merge Conflicts

***
## Lecture 14

### MongoDB

* Indexes: B-Trees
* CAP Theorem:
	* Consistency
	* Availability
* Documents order hierarchically  
* Type and Case Sensitive

***
## Lecture 16

### MongoDB Indexes

* Use mongo Ruby gem to access MongoDB
* Convert created_at from string to times object
	* ``` t = DateTime.parse(“Sun Feb 15 02:41:32 +0000 2015”)```
	* ``` return t.to_time.utc ```
* Coordinate fields: used for geospatial queries
* ```explain``` function will return information about how DB will process any given query
* Indexes are stored on collections, not databases

***
## Lecture 17

### More on Indexes

* Can greatly reduce the number of documents that need to be examined to satisfy a query
* Index Cardinality
	* Number of possible values for an indexed field
		* A field like **employment status** has low cardinality since it has two values yes/no
		* Where as **name** has high carnality
	* In general you only want indexes on high cardinality fields
* Compound indexes can be difficult
	* Example sort by : ```user.created_at``` (oldest to youngest); ```created_at``` (most recent tweet to oldest tweet)
	* Reverse sort is: ```db.tweets.find().sort({‘user.created_at’:-1,’create_at’:1})```
	* Enable different queries:
		* Point Queries: search for a single value, then traverse index (either direction)
		* Multi-Value Queries: search for a range of values
* Full-Text Indexes
	* Support for a full text search
	* Only one full-text index per collection
* Geospatial Indexes
	* Cartesian Index
	* Spherical Index: 2dsphere
		* GeoJSON format
			* Supports points, lines, and polygons

### Map Reduce

* Ability to create a new collection from an old collection
	* ```db.tweets.mapReduce(map, reduce, {out: "users”});```

***
## Lecture 18

***
### Apache Solr

* Lucene
	* High-performance text search engine library
	* Inverted index - store the keywords of the documents in the index
* CU FCQ - Example
	* Searches three tables
	* DB - 100,000 rows
	* Excel to DB
* Solr has a REST API
	* Runs as a server

***
### Redis

* Key Value Store “Data-structure server”
* Not a database replacement
* Use for fast real-time data applications

***
### Kafka

* How to process data coming in real time.
	* Distributed
	* Fault-tolerant
	* High-throughput	
	* Publish-subscribe
	* Message system
* Publish - Subscriber
* Kafka relies on ZooKeeper for distributed falt tolerance

***
## Lecture 19

### Kafka Demo
* Fake twitter data through a framework stack
* Output to a web client

### Memcached

* Distributed memory object caching system
* Large hash table
	* Keys up to 250 bytes
* Data is disposable
* Cluster is flat

### Document DB (On Azure)

* Schema-free
* Indexing database
	* Automatically index documents added to DB

***
## Lecture 20

### Neo4J

* Graph based database
	* NoSQL
	* Whiteboard Friendly
		* Easy visualization
	* Relationship Focused
		* Edges are most important
	* Java Based
		* Open Source
* Fast for associative data sets
* Typically implemented on a single server versus a cluster

### HBase

* Hadoop Database
	* Open source distributed column-oriented
* Provides big table capabilities on top of Hadoop
* Table schema defines only column families
* Each cell value of the table has a timestamp
	* Automated versioning
* Used for lot of incoming data
	* Large amount of client/request

***
## Lecture 21

### Riak

* Key-Value Store Database
* NoSQL
* No Master node
	* Every node is a Master & Slave
* Scaling: Value of key defines which node the key will be stored on
* Written in Erleng

### Cassandra

* Scaled NoSQL database
* Elastic scalability
* Always on architecture
* Fast linear-scale performance

### Indexing in Cassandra

* Insert rows similar to SQL
* Composite Columns w/ primary key
* Clustering column sorts the data
	* One or more partition keys
	* Zero or more clustering column
* Secondary Indexes	
	* Cassandra provides support to add indexes over column values

***
## Lecture 22

### Javascript Closures and Design Patterns

* Scope
	* Example
* Closure
* Module Design Pattern
* Inheritance vs Prototype
* this
	* new Name()
		* refers to object it returns
	* explicit
	* implicit
	* default

### Ruby on Rails

* Ruby
	* No default function overloading
	* Able to return multiple values
* Rails framework
	* Gem setup

### Flask

* Micro framework
* Written in Python
* Testing is made ease with Flaskr

***
## Lecture 23

***
### Hadoop
* MapReduce
* Master/Slave

***
### Spark
* Fast Data Sharing
* MapReduce+
* Cluster Wide Caching

***
### Apache Storm
* Stream Processing
* Guaranteed Message Processing

***
## Lecture 24

***
### React

* Released by Facebook
* Maintains a virtual DOM
* One-way state binding
* JSX
	* Creates javascript objects using html syntax


***
### Sinatra

* Presented

***
### Flux

* Single directional data flow
* Built by Facebook to combat scalability of MVC

***
## Lecture 25

### Google Cloud Platform

* Support Python, Java, PHP and Go 
* Google handles shading, load balancing, traffic splitting, elasticity, ect . . .
* Use Google fiber between Data Centers
* Data transmitted and stored in encrypted form 
* Three tiers of Cloud Storage
* Cloud SQL
	* Pay per use

### Docker

* Open-source engine that automates deployment of apps into containers
* Fight against dependency discrepancy
* Containers
	* Created from images
	* Isolated environment

### Capistrano

* Automated Server Deployment
	* Uses Rake DSL for tasks
	* Written in Ruby
* Can create custom tasks 
* Automate task for pulling repo to server

***
## Lecture 26

### Turf

* GeoJSON
* More for analysis than visualization

### JavaSript InfoVis Toolkit

* Library to create interactive data visualization on the web
* Composeable:
	* Combine multiple visualization into one
* Data is stored in static JSON objects

### Flask

* BSD
* Very extendable
* Uses ```pip install flask```

***
## Lecture 27

### D3 

*	select
* bind

### Leaflet

* Layering
* MultiPlatform
* Call maps

### Vega

* Presented

### Epic

* Epic Collect (Data Storage)
	* Keyword Tweets
	* Context Tweets

***
## Lecture 28

### JavaScrip Async and Promises

* Event Loop
* Callback
* Promises
	* Chain

### Titan

* Graph Database

### Amazon Web Services

* Cloud computing
* Computing
* Networking
	* DNS
	* VPC
	* Amazon DirectConnect
* Storage
* DynamoDB - Precursor to Cassandra

### Epic

* Use Hadoop to sort
* Solr 

***
## Lecture 29

***Final Presentations***

