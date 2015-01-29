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
* Install express
* Install necessary middleware
