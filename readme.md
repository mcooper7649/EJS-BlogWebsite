### EJS BLOG Challenge
---

## Challenge Setup
---
    - Download Starting File and Move to Root Directory
    - Open App.js in VScode and expand folders
    - Styles are already configured
    - Ignore the .DS_Store Files 
    - Header/Footer already have code and will be added via EJS partials
    - App.js has the require consts already added
    - Content is already specified
    - Const app has been declated
    - View Engine for EJS has been configured
    - BodyParser URL encoded has been added already
    - Public Folder has been declared for express
    - Port is already configured for app.listen
    - NPM has already been initialized, as you can tell with the package.json files
    - Dependencies have already been specified but need to be installed
    - Install the node modules listed by simply typing npm install from the package.json directory

## Challenge #1
---
    - When you head over to localhost:3000, it will render the home view and you will have an h1 that displays "Home"

    ```
    app.get("/", function(req, res){
    res.render("home");
    });
    ```

    - Needed res

## Challenge #2
---
    - In App.js we have 3 content constants, we need you to get the homeStartingContent to be rendered ont he home.ejs page went "/" route is accessed.

    app.js
    ```
    app.get("/", function(req, res){
        res.render("home", {
            homeContent: homeStartingContent
        });
    });
    ```

    home.ejs
    ```
    <h1>Home</h1>
    <p> <%= homeContent %> </p>
    ```
## Challenge #3
    ---

    - Our Footer and Header already have some code including bootstrap, css folder, navbar, and footer information.

    - Use EJS Partials, to add header and footer to existing Home page

    home.ejs | How I added partials
    ```
    <%- include("header") -%>

    <h1>Home</h1>
    <p> <%= homeContent %> </p>

    <%- include("footer") -%>
    
    ```

## Challenge #4
    ---

    - Create a new folder inside the views folder called "partials"
    - Move your footer and header to partials folder
    - Update Code in home file
    `` <%- include("partials/footer") -%> ``

## Challenge #5
---
    - Add About and Contact Page to be rendered using our partials and add content for each page like we did the home page

    - Solution | Copied configuration from app.js get route and updated view, and json object with correct vars. Then I updated Header Partial as it had links that didn't match correct view/route

## Challenge #6
---

    - This challenge was changing the navbar. Did it in previous challenge.

## Challenge #7
---
    - Setup localhost:3000/compose to render
    - Add Partials
    - Add h1 that says "Compose"
    - Add text input and button that says "Publish"
    

    compose.ejs
    ```
    <%- include("partials/header") -%>


    <h1>Compose</h1>
    <input type="text" name="compose" id="">
    <button type="submit">Publish</button>

    <%- include("partials/footer") -%>
    ```
    
    app.js
    ```
    app.get("/compose", function(req, res){
    res.render("compose");
    });
    ```

## Challenge #8
---
    - Setup the text input so if someone hits publish the content is logged to the console.

    - Solution was create a post route on the app.js and console the req.body.composeItem

    - Side note | app.use(bodyParser.urlencoded({extended: true}));   This needed to be after app const but not at the end of the file to for bodyParser to be used.

    app.js
    ```
    app.post("/compose", function(req, res){
    console.log(req.body.composeItem);
    });
    ```

    compose.ejs
    ```
    <form action="/compose" method="post">
    <input type="text" name="composeItem" placeholder="New Item" autocomplete="off">
    <button type="submit">Publish</button>
    </form>
    ```


## Challenge #9
---

- We are going to add a Title Input and Post Input to our compose page.
- Add bootstrap to both input boxes, Title is single-line while post is multi-line
- Publish Button needs to be Blue and Match the example
- A Label for each input field


## Challenge #10
---

- On the app.post route, we need to create an object to pass both the title and body of the post

```
app.post("/compose", function(req, res){
 const post = {
   title: req.body.composeItemTitle,
   content: req.body.compostItemPost
 }
});
```

## Challenge #11
---

- Create a global variable array called "posts" and store the post we created there.

- Redirect to the home page and console the posts array and you should see your array

## Challenge #12
---

1. Delete all console.logs we have in the app except app.listen

2. log our posts array from the home.ejs file


## Challenge #13
---

3. Make our blog log just the titles of each item in our posts array.

4. Create a for loop that console logs every title in the arary. 


## Challenge #14
---

1. Instead of using a basic forloop, lets use a much easier way to loop, the forEach();

2. Add the forEach loop to replace your traditional for loop. 

forEach loop with EJS added

```
<% posts.forEach(post => { %>
    <%  console.log(post.title) %>
    <% }); %>
```

## Challenge #15
---

1. Using loremipsum.io create 3 posts but have them rendered instead of logged on our home.ejs page.

```

   <% posts.forEach(post => { %>
        <h1><%= post.title %></h1> 
       <p> <%= post.content  %></p>
         <% }); %>

```

##  Express Routing Parameters
---

1. Using Express Routing I want to be able to type localhost:3000/posts/randomname, I want nothing to happen on the page but I want to see the randomname logged. 


```

app.get("/posts/:postTitle", function(req, res){
  console.log(req.params)
  });

```


## Challenge #16
---

rs in server console to restart nodemon to reset our arrays.

1. Create a new single blog post using loren ipsum.

2. I want to be able to type localhost:3000/post/titleOfTestPost  then I want "Match found" return from the server console.



## Challenge #17
---
3. We need to compare the req.params to our post.Titles and if it does, return "Match Found" from the server.



## Challenge #18
---

1. log "Not a Match" if not match found.

2. Lets add the utility library lo-dash | lodash.com

3. Read the documentation and implement the documentation.

4. Turn all strings into lowercase, it will also ignore hyphens and underscores.

5. I want "Another-Post" url to return "Match found" when we search for a compose we made with the Title "Another Post"

## Why Lodash?
---

[lodash](lodash.com)

Lodash makes JavaScript easier by taking the hassle out of working with arrays, numbers, objects, strings, etc.
Lodash’s modular methods are great for:

Iterating arrays, objects, & strings
Manipulating & testing values
Creating composite functions

```
npm i lodash
var _ = require('lodash');

_.lowerFirst() //add to posts app.get

```


## Challenge #19
---

1. Instead of logging "Match Found" lets render the actual page.

2. EveryPage we create should load if found. Just with that blank post information. Using just Express routing parameters and ejs.

app.js
```

app.get("/posts/:postTitle", function(req, res){
  const requestedTitle = req.params.postTitle;
  posts.forEach(post => {
    const storedTitle = post.title;
    if (_.lowerCase(storedTitle) === _.lowerCase(requestedTitle)){
      console.log("Match Found!")
      res.render("post",{
        title: post.title,
        content: post.content

      })
    }
  });
});

```

post.ejs

```

<%- include("partials/header") -%>

<h1><%= title %></h1> 
<p> <%= content  %></p>

<%- include("partials/footer") -%>
```

## Challenge #20
---

We want our homepage to automatically truncate the amount of characters that a post displays for the blog body. 

1. 100 Character Limit

[HowToTruncateString](https://stackoverflow.com/questions/1301512/truncate-a-string-straight-javascript)


```

 <% posts.forEach(post => { %>
        <%  var length = 100; %>
        <%  var myTruncatedString = post.content.substring(0, length); %>
        <h1><%= post.title %></h1> 
       <p> <%= myTruncatedString  %></p>
         <% }); %>
```



## Challenge #21
---

We the home Page to have ... dots after the truncation on the Home page and also a link that says "Read More" that when clicked will take you to the page.

```
        <p> 
           <%= myTruncatedString  %>
           <a href="/posts/<%= post.title %>">
               Read More
           </a>
        </p>
```