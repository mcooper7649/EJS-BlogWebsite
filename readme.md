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