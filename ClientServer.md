Vocab:
    server - a program (or hardware) that accepts and responds to requests from a client
    client - a program (or hardware) that accesses a service made available by a server
    middleware - software that enables communication of data between domains -> For example, www.myapp.com can talk to www.apiformyapp.com
    router - determines how to handle an incoming HTTP request
    route - the actual path that handles a request: localhost:3000/helloworld
    controller - receives the request from the router and decides what to do with it
    endpoint - a function like POST or DELETE available through shared base routes: /user/post-data or /user/delete-data
    database - a structured set of data held that is accessible in various ways
    database table - used in relational databases to store data; a flat file with vertical columns and horizontal rows
    data model - server code that mirrors the structure of a database table
    encryption - the conversion of data into encoded data to hide its true value: "mypassword" -> "2XKLJlkjasdlfl83"
    statelessness - the idea that a client and server forget each other after each request/response lifecycle
    session - a timed meeting between two different devices or applications
    token - allows a server to identify a client more easily between requests
    authentication - the process of comparing credentials provided by a client with those found in a database
    SQL - a language used to query a relational database
    migration - the process of updating a database table if a data model changes

Dependency:
    A dependency is a necessary requirement for a class or interface to use.
    Think of this analogy:
        * If you have a TV remote, you also need the batteries.
        * You cannot use the remote without also using those batteries.
        * Furthermore, you cannot continuously reuse that remote unless you also continuously reuse those batteries.
        * If your batteries fail, you can no longer use your remote.

run npm init in terminal
change name and description in package.json
add the following to scripts:
    "start": "node app.js",
    "dev": "nodemon"
run npm update
npm install 

- Dependencies:
    - bcrypt - Password-specific hashing that protects your password from being stored in plain text
    - dotenv - Allows developers to safely store configuration data
    - express - A web framework for Node.js that allows routing and processing HTTP requests
    - jsonwebtoken - A compact and self-contained way for securely transmitting information between parties
    - pg - A dependency for working with Postgres
    - pg-hstore - A dependency for working with Postgres for advanced functions with Postgres
    - sequelize - A tool that allows us to map models, pass data, and complete queries with a database

- Example of setting up app.js:
const Express = require("express"); //Line one: requiring the use of the "express" npm package installed in dependencies
const app = Express(); //Create an instance of "express". This is actually firing off top level "Express()" function, which was exported by the Express module. This allows the ability to create an Express app.

app.listen(3000, () => { //app.listen will use express to start a UNIX socket and listen for connections on the given path. The parameter (3000) indicates that the path will be "localhost:3000".
    console.log(`[Server]: App is listening on 3000.`); //This callback function allows us to see what port the server is running on.
});

Open server in terminal and type "npx nodemon"
you should see the following in the terminal:
    [nodemon] 1.19.4
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] watching extensions: js,mjs,json
    [nodemon] starting `node app.js`
    [Server]: App is listening on 3000.

* Postman:

* About Postman:
    Building a back-end is a little more abstract than building a front-end. In a web application, we can see changes as we make them: a color, a button, an image. With the back-end, we need a way to test our code as we build it to ensure that we are on the right track. Postman is a great tool for that job.

* Helpful Features:
    Postman provides back-end developers with an enormous amount of value, including the following items:

        1. Ability to test endpoints.
        2. Can fully log into an application and save data to a database without needing sign in or sign up forms on the client side.
        3. Code can be written and run directly inside postman to control external servers, devices, etc.
        4. Collections of API endpoints can be saved and tested simultaneously.

* HTTP request methods:
    HTTP defines a set of request methods to indicate the desired action to be performed for a given resource. Although they can also be nouns, these request methods are sometimes referred to as HTTP verbs. Each of them implements a different semantic, but some common features are shared by a group of them: e.g. a request method can be safe, idempotent, or cacheable.

    GET 
        The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.

    HEAD
        The HEAD method asks for a response identical to a GET request, but without the response body.

    POST
        The POST method submits an entity to the specified resource, often causing a change in state or side effects on the server.

    PUT
        The PUT method replaces all current representations of the target resource with the request payload.

    DELETE
        The DELETE method deletes the specified resource.

    CONNECT
        The CONNECT method establishes a tunnel to the server identified by the target resource.

    OPTIONS
        The OPTIONS method describes the communication options for the target resource.

    TRACE
        The TRACE method performs a message loop-back test along the path to the target resource.

    PATCH
        The PATCH method applies partial modifications to a resource.

Routes:
Routing refers to determining how an application responds to a client request to a particular endpoint. An endpoint is a path and a specific HTTP request method attached to that path (GET, POST, DELETE, PUT).

Diagram of routes:
https://elevenfifty.instructure.com/courses/810/files/153229/download

Routes Analysis:
A GET request is made to localhost:3000/test.

When the route is requested, Express finds the method for the specific route. We used this method with the previous lines of code we just added.

So when we go to the /test endpoint, we fire off an Express function res.send.

res (short for response) handles packaging up the response object.

The .send() method does the job of sending off the response.

Example of controller:
const Express = require("express"); //We import the express framework and store it in the variable "Express". This instance becomes our gateway to using Express methods.
const router = Express.Router(); //We create a new bill called router. Since the Express variable gives us access into the express framework, we can access express properties and methods by calling express.methodName(). Therefore, when we call the "Express.Router()", we use the "Express" variable to access the "Router()" method. "Router()" method will return a router object. More info here -> https://expressjs.com/en/4x/api.html#router

router.get('/practice', (req, res) => { //We use router object by using the router variable to get access into the "Router()" object methods. "get()" is one method in the object, and it is called here. This method allows us to complete an HTTP GET request. 2 arguments are passed into the ".get" method. The first argument, '/practice', is the path. Similar to how we used the '/test' path to test out Postman previously. The second argument is an anonymous callback function. This is also sometimes called a "handler function". This function will be called when the app recieves a request to the specified route and HTTP method. The app "listens" for requests that match the specified route(s) and method(s), and when it detects a match, it calls the specified callback function.
    res.send('Hey!! This is a practice route!') //Inside our callback function, we call "res.send()". "send()" is an express method that can be called on the "res" or response object. Our response parameter is just a simple string.
});

module.exports = router;//We export the module for usage outside of the file.

Databases:
A database is simply a persistent storage method for any data. Data is stored on a computer in files, which are formatted specifically for a type of database. The way this works is an application runs on a computer that has been designed to manipulate the formatted files. Think of a Database file similar to a Word Document, Excel file, or even a JavaScript file. It has a specific purpose, it is structured for the program meant to open/run it.

In order to get deeper into routes and the server, we'll need to start working with a database. In this module, we'll discuss two types of databases, examples, and some common terms associated with them.

SQL
In addition, relational databases use SQL (Structured Query Language) to manage the information. SQL is most often pronounced "Sequel", but you may also hear pronounced "S - Q - ELL". SQL is a language of its own, using commands to create, delete, change, or display information from the database. Relational databases are often called "SQL databases" for this reason. We will teach you about SQL in a future lesson.
You can read more about SQL databases here:
https://www.openlogic.com/blog/what-sql-database

Object Example:
{
    "person": {
        "1": {
            "firstName": "Aaron",
            "lastName": "Ofengender",
            "height": "70in",
            "eyeColor": "brown",
            "glasses": true
        },
        "2": {
            "firstName": "James",
            "lastName": "Smith",
            "height": "65in",
            "eyeColor": "blue",
            "glasses": false
        }
    }
}
More info here -> https://aws.amazon.com/nosql/

PostgreSQL History
PostgreSQL, also commonly called "Postgres", was originally created in 1986 at the University of California-Berkeley by a professor and some of his graduate students. Postgres was one of the first major attempts at creating a relational database system. Over the course of the next decade, it underwent several major updates and revisions within the university, and a version of it was eventually purchased by IBM in 2001. In 1996, however, some developers outside of the university jumped on the open-source project and began a complete re-write of the system, including replacing its native, proprietary language with SQL. This culminated in 2004 with PostgreSQL 6.0, the first version as we know it today. Still one of the most-widely used database systems in the world, it has continually been open-sourced and updated, now currently at version 10.3.

PG Admin
PG Admin was originally created as PostgreSQL manager in 1998, a Windows-based GUI tool to manage PostgreSQL databases. Several versions of the program later, PG Admin 4 was released in 2016. Written in C++, it focuses on cloud-based databases while also providing support for local and physical databases. PGAdmin, now PGAdmin 4, is the most popular Open Source administration and development platform for PostgreSQL.

Postman password - 16e178946be14ab9abd46a256ad6b0ce
PgAdmin password - Max2002

What is Sequelize?
Sequelize is a promise-based ORM (Object-Relational-Mapping) for Node.js. It supports several different SQL dialects, including PostgreSQL, MySQL, SQLite, and MSSQL. Essentially, one of the main features of Sequelize is that it allows developers to communicate between the server and the database more fluidly. Here (https://blog.bitsrc.io/what-is-an-orm-and-why-you-should-use-it-b2b6f75f5e2a) is an article talking about the importance of an ORM.

Diagram: https://elevenfifty.instructure.com/courses/810/files/153238/download

MVC:
In this chapter, we'll walk through several modules that will teach how to build controller methods and routes that make requests containing data. Those requests will post, update, get, or delete data in our Postgres database and return that data to the client in the form of a response. To write this code, we'll use a Model-View-Controller pattern, so we'll introduce you to MVC at this time.
The Model-View-Controller Software Pattern

MVC is a common software pattern found in many programming languages and applications. Take a look at a diagram of MVC to start getting an idea of how it works: https://elevenfifty.instructure.com/courses/810/files/153233/download

Views
For this chapter, we won't be dealing with the view, but we'll say that the view/client would be sending requests, receiving responses, and working to display the data to users. For a temporary client, we'll use Postman in lieu of a View.

Controllers
It's good to think of the controller as something that handles the heavier logic in the application. A controller is usually a method or methods that will handle some or all of the following things:

Receiving the incoming request depending on the route.

Processing the type of incoming request: GET, POST, PUT, DELETE.

Collecting the data from the incoming request.

Working with the model to ensure that the requested data matches the types in the model and the database.

Creating, updating, reading, or deleting objects in the database.

Sending off the response for the incoming request.

Models
Coding models are usually considered to be representations of the data being handled. Models can do the following:

Represent the data being stored in the database.

Dictate the types of data that will be stored (string, boolean, integer etc).

Handle some basic business logic in an application, such as a character limit for a string being stored in the db, formatting for date and time details, and many other things that shape the data in the database.

Used by the controller to handle logic.

Endpoints & Routes
As mentioned in a previous module, when an HTTP request comes in, it hits a route and finds the proper endpoint. When the router finds the proper endpoint, the proper controller method is fired, and the controller method handles any necessary logic. To practice learning about endpoints, controllers, and models, we'll be building the following endpoints in the modules ahead:
    http://localhost:3001/user/create - POST
    http://localhost:3001/user/login - POST
    http://localhost:3001/journal/create - POST
    http://localhost:3001/journal - GET
    http://localhost:3001/journal/mine - GET
    http://localhost:3001/journal/:title - GET
    http://localhost:3001/journal/update/:id - PUT
    http://localhost:3001/journal/delete/:id - DELETE

Rationale
Essentially, we will use models to define the data that we want to store. The model in our server will closely mirror the data table in our database. Consider the following diagram: https://elevenfifty.instructure.com/courses/810/files/153231/download

Notice how the user model in the server has the following properties: username, password, age, and isMarried.These are all properties of a user model that will eventually show up in the database. Notice how the Postgres database table has columns for these properties.

The model and the db table are not exactly the same though. Sequelize will do the following under the hood:

Add an id that increments automatically and without repeating (1, 2, 3, 4, etc.)

Add a timestamp for when the row was created.

Add a timestamp for when the row is updated.

Controllers:
A Controller controls the requests of the user and generates the appropriate response which is fed to the View (Postman).  The user interacts with the View (Postman), which generates the request.  The request is handled by the Controller.  The controller renders the View (Postman) with the Model data as a response.

It's good to think of a controller as something that handles or 'controls' the heavier logic in the application. A controller is a method or methods that will handle some or all of the following things:

Receiving the incoming request depending on the route.
Processing the type of incoming request: GET, POST, PUT, DELETE.
Collecting the data from the incoming request.  
Working with the model to ensure that the request data matches the types in the model and the database.
Creating, Updating, Reading, or Deleting objects in the database.
Sending off the response for the incoming request.

Overview
With Postman, we have the ability to create an account, login to an account, and receive a token. In a little while, we will use those routes in the DOM. However, for now, let's do some server work and prepare it for authenticated requests.

 

What is an Authenticated Route?
An authenticated route is another way of saying a protected route. There are parts of our database and site that we only want certain people to be able to access, and only certain parts that those certain people are allowed into. When you login to your email or a site like Facebook, you're being taken to an authenticated route: your email inbox, your Facebook feed, etc. While their authentication processes are undoubtedly far more advanced and complicated than what we'll do, the idea is the same: keeping out any unauthorized traffic or malicious users.

 

How Do We Do It?
We need to write a middleware function that acts as a gate between the client and the server. This middleware is going to look for and look at our token in the request. If the request has a token, it's allowed to pass through the gate to reach the server and get data from Postgres to be returned or saved for a specific user. If not, the request is rejected.

 

Think back to the example about the bar from earlier. In this context, the bar is the route we want to authenticate. After you pay your cover and get your stamp, you go inside and order a drink from the bartender. First, the bartender has to check that you have a stamp, then check your ID to make sure that you're old enough to drink. This second step is the new middleware function that we're going to create: validation.

 

We can even take this one step further: Let's say the bar uses different stamps for different nights of the week. The doorman was only checking to make sure that you had a stamp; the bartender will check to make sure it is TONIGHT's stamp, not the previous night's. Remember that when we create our tokens, we give them an expiration date, so our new middleware function needs to not only verify that the token belongs to the user that it was assigned to, but also verify that the token is still valid.