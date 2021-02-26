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


