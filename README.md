# Data Engineering Lecture Notes 

# Spring 2015

## Lecture 1

***
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