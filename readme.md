# [LIVE PROJECT](https://mylibrary-fullstack-mern.herokuapp.com/)

## This is the full stack web development. In this we will be creating a library application called MyLibrary.
-----------
- This application will run on Node.js, Express, and MongoDB.
- During this we will learn how the backend works.
- How to create our own backend. How to connect your server to a database.
- How to deploy a web application.
- And, how to style a professional looking website.
- By the end of this we will have a complete understanding of the backend of a website and be able to create our own web applications.

# How Backend works ?
As we already know, the web is made up of two main parts. The frontend and the backend. The frontend is concerned with presentation and is fairly easy to understand since it is what we interact with daily on the web. The backend, on the other hand, is all of the parts of the web that users do not directly interact with. In this video we are going to discuss the basics of how the backend of a website works by tracing all of the steps that the backend must go through from the moment it receives a request to the point it sends a response back to the client.

Starting at the beginning the server will receive a request from a client in the form of a URL. From this URL the server can get almost all of the information it needs in order to process a request. Let's break apart a typical URL. At the beginning we have the protocol for the request. The only thing that the protocol does is tell the server if the request is encrypted. HTTP is for standard non-encrypted requests, and HTTPS is for encrypted requests. Other than telling the server if the response is encrypted or not the protocol doesn't affect the way the server handles requests and can be ignored. Next, we have the host, also known as the domain name. Again, this is not important to worry about for the server since all it does is tell the internet which server to send the response to. Each server has their own particular host, so once the request actually gets to the server the host does not matter since all requests for the server will have the same host. For example, youtube.com is the host for the YouTube server, so the YouTube server already knows that all requests it gets will have the host youtube.com. This means that we can safely ignore the first half of the URL which leaves us with the last two sections of the URL. The path and the query string. The path tells the server what the client wants and defines which section of code on the server should be run in order to get the correct response. Essentially the server is broken down into a bunch of different sections which all correspond to a specific path. Lastly the query string is used by the specific section of the server to alter the response. The query string is broken down into specific query parameters which can augment the way that the server responds to a request for a specific path. For example YouTube uses the same path when you search for a video, but the query string contains a search_query parameter which tells the server what you searched for so it can respond with what you want.

The URL alone is not enough to tell the server exactly what it needs to do, though. It can tell the server which section to look for and how to alter that section based on the query parameters, but that section of the server is broken down even further into multiple different parts. To determine which part of that section the server should run it needs to use an action which is passed along with the URL. This action can either be GET, POST, PUT, or DELETE. By combining the action and the path the server can find the correct part of the correct section that it needs to run. It can then use the query parameters to alter the response of that particular part and section.

Normally the response from the server will be an HTML page that is dynamically generated based on the request from the client. This is why when you go to the YouTube search page it always shows you the same page, since it has the same path and action, but the videos that are returned from your search are different based on the query parameter for your search.

Another important thing to note about a server is that it is only accessible to the outside world through the sections that it defines. This means that you can store any secure information on the server and it will be safe as long as it is not exposed through a specific path. This is why it is safe to have a database and website running on the same server since the server only chooses to expose the website and not the database. Essentially the server acts as a barrier between the outside world and all the parts of a website.

# What is REST ?
If you have used any modern website, then chances are you have interacted with a website that uses REST. Even YouTube uses RESTful URLs on its site, but what exactly is REST? For starters, REST stands for Representation State Transfer and is just a fancy way of saying that a server responds to create, read, update, and delete requests in a standard way. The idea behind REST is to treat all server URLs as access points for the various resources on the server. For example in this URL, http://example.com/users, users represents the resource that the server is exposing. As mentioned earlier, REST needs a way to create, read, update, and delete these resources and it does so with the following five URLs.
- http://example.com/users
- http://example.com/users
- http://example.com/users/1
- http://example.com/users/1
- http://example.com/users/1

The first two URLs do not have an ID so they act on the entire user's resource, while the last three URLs do have an ID in their URL and thus act on only a single user resource, but as you may notice there are only two distinct URLs. That is because REST uses the four basic HTTP actions, GET, POST, PUT, and DELETE to determine what to do with each URL. If we add in those actions to the URLs it is much easier to see what each of the URLs do.
- [GET]     http://example.com/users
- [POST]    http://example.com/users
- [GET]     http://example.com/users/1
- [PUT]     http://example.com/users/1
- [DELETE]  http://example.com/users/1

The first URL we have is the GET users URL, and it is used to get a list of all users. In REST when a GET URL does not have an ID it acts upon the entire resource and will always return a list of every item in that resource. The GET action in REST corresponds with reading data.

The second URL, which is almost identical to the first, is used to create a new user. In REST the POST action corresponds with creation, and should always be used on the entire resource by not using an ID in the URL.

The third URL is another GET URL, but this URL is for getting only a single user based on the id that is in the URL. The ID portion of the URL is used by REST to determine which resource from the collection of resources it should act upon. In the case of this URL it is used to return the user with that ID.

The fourth URL is the most confusing of them all, but it is used to update a user with the given ID. The PUT action in REST corresponds with update and works very similarly to POST, but instead of creating a new resource it updates an existing resource.

Lastly, we have the most straight forward URL of them all which is for deleting a user with a specific ID. The DELETE action in REST does exactly what you would think and deletes the resource with the given ID.


In order for a website to use REST, the URLs do not need to be formatted exactly the same as above. For example using these URLs would still be considered RESTful, but most applications will use the previously mentioned URLs.
- [GET]     http://example.com/users
- [POST]    http://example.com/users
- [GET]     http://example.com/users/details/1
- [PUT]     http://example.com/users/update/1
- [DELETE]  http://example.com/users/delete/1

The only thing that matters with REST is that the URLs used represent a resource, in this case a user, and that they support creating, reading, updating, and deleting from that resource using the HTTP actions GET, POST, PUT, and DELETE.

# What is MVC(Model, View, Controller) ?
MVC is the most popular architecture for building complex web servers. It is used by many frameworks, and implemented into nearly every modern web application. In this video I will cover what MVC is, how it works, and why you should use it.

MVC stands for Model, View, Controller. It is used to define how these three different entities can interact with each other.

The Controller handles user requests and delegates information between the Model and the View. It only deals with requests, and never handles data or presentation.

The Model handles data validation, logic, and persistence. It interacts directly with the database to handle the data. The Controller will get all of its data information by asking the Model about the data.

The View handles presenting the information. It will usually render dynamic HTML pages based on the data the model fetches. The Controller is responsible for passing that data between the Model and View, so that the Model and View never have to interact with each other.

### <b> Step 1: In this we will be setting up the base of our project by:
1. Setting up Express
2. Hooking up MongoDB
3. Setting up local ENV variables
4. Creating a base layout HTML file
5. Setting up our MVC folder structure</b>

### <b> Step 2: In this we will be setting up the author's Index/Create/New routes. To do this we will need to:
1. Create an author model
2. Create an author controller
3. Create author views
4. Interact with our database to find and create authors
5. Handle validation errors
6. Setup a shared page header</b>

### <b> Step 3: In this we will be setting up the book's Index/Create/New routes. To do this we will need to:
1. Create a book model
2. Create a book controller
3. Create book views
4. Interact with our database to find and create books
5. Handle validation errors
6. Setup file upload
7. Store uploaded files</b>

### <b> Step 4: In this we will be improving the file upload process by:
1. Implementing FilePond
2. Adding a file upload preview
3. Implementing drag and drop upload
4. Storing files in the database for Heroku</b>

### <b> Step 5: In this we will be setting up the author's Show/Edit/Update/Delete routes. To do this we will need to:
1. Add routes to the author's controller
2. Add views for the author's views
3. Add data validation checks for deletion
4. Create a delete form
5. Interact with our database to update and delete authors
6. Finish the navigation for authors in our views</b>
### <b> Step 6: In this we will be finishing the backend of the project by setting up the book's Show/Edit/Update/Delete routes. To do this we will need to:
1. Add routes to the book's controller
2. Add views for the book's views
3. Interact with our database to update and delete books
4. Finish the navigation for books in our views
5. Polish our backend code and views</b>
### <b> Step 7: In this we will be creating all of the base CSS styles for our entire application. These styles will include
1. Setting up our CSS structure
2. Setting up our background and text colors
3. Creating the header styles
4. Creating the button styles
5. Styling the page headers</b>
### <b> Step 8: In this we will be creating all of the form and file upload CSS styles for our entire application. These styles will include
1. Creating the basic input styles
2. Setting up our overall form layout styles
3. Styling the file upload element
4. Overriding the default select box option styles
5. Persisting these styles across the entire application</b>
### <b> Step 9: In this we will be finishing the entire MyLibrary application. To do this we need to:
1. Finish styling our author search/show page
2. Style the file upload box
3. Style the book show page
4. Create a partial for our book grids
5. Clean up any remaining styles</b>

<br>
<i>Web Dev Simplified - Full Stack Web Development Course

https://www.youtube.com/playlistlist=PLZlA0Gpn_vH8jbFkBjOuFjhxANC63OmXM

live project at: https://mylibrary-fullstack-mern.herokuapp.com/