# MERN Stack: Full Build Documentation 

This is some good ol' handmade documentation for a complete, full CRUD application built in a stack refered to as 'MERN'(MongoDB, Express.js, React.js, Node.js). 

##  First Thing's First

  We need to create some files. Let's begin by opening up our terminal. 

     ctrl+space 

  Next, we'll need to change to our root directory. In this instance, we'll use our Desktop as out root directory. *Type the following command*. 

     cd Desktop 

  Now that we are at our Desktop, lets create a file(i.e. 'directory'). 

     mkdir name-of-direcotry 
    
  Alright, now that we've create a folder to store our project in, we'll need to move into that file.

     cd name-of-directory 
    
  Now that we're in our project file, we'll need to create a folder for our frontend and our backend.

     mkdir name-of-directory-frontend name-of-directory-backend  
    
  This will give us places to store our React.js files(frontend) and our Express.js files(backend). Let's begin by creating our backend. First, we'll need to 'change directories' or 'cd' into our backend folder. *Hit this command in your terminal*. 

     cd name-of-directory-backend 

  Rad! We're in our backend folder. Let's create some files so we can write some code! To create files, we'll start our terminal command off with **touch** followed by the file name.type. For now, we'll create our *.env* and our *server.js*

     touch .env server.js 
  
  Let's utilize Node.js and install our node project so we have a place to store all of our node packages.
  
      npm i init -y 
      
  And for our dependencies
  
      npm i dotenv mongoose express cors morgan
      
      
 Now that we've created all the necessary files, let's opem up our project in our favorite text editor. For me, it's *VS Code*! You can either drag your folder from your desktop to your text editor app or if you're running *Vs Code* like me, you can tyoe this into your terminal.
 
    code .


Alright! We finally made it! But before we begin to code, we'll need to set up our environment file with a couple of key requirements. We'll need to store our Database URL connection string in here as well as our local viewing port. 

    DATABASE_URL=mongodb+src://....
    PORT=#3001
    
Let's get our server started! In *server.js*

    ///////////////////////////////
    // DEPENDENCIES
    ////////////////////////////////
    // get .env variables
    require("dotenv").config();
    // pull PORT from .env, give default value of 3001
    const { PORT = 3001 } = process.env;
    // import express
    const express = require("express");
    // create application object
    const app = express();

    ///////////////////////////////
    // ROUTES
    ////////////////////////////////
    // create a test route
    app.get("/", (req, res) => {
      res.send("hello world");
    });

    ///////////////////////////////
    // LISTENER
    ////////////////////////////////
    app.listen(PORT, () => console.log(`listening on PORT ${PORT}`));
    
Let's see if we can birth this e-baby into existence! PUSH!!!

In your text editor's integrated terminal, run the *nodemon* server or if you updated package.json you can run *npm start* and make sure you see "Hello World" when you go to **localhost:3001** in your web browser.


Siquness! The World says 'Sup!'. Let's update our *server.js* file to include a database connection. 

    //... more code above

    const { DATABASE_URL, PORT = 3001 } = process.env;

    const express = require("express");
    // create application object
    const app = express();


    // import mongoose
    const mongoose = require("mongoose");

    ///////////////////////////////
    // DATABASE CONNECTION
    ////////////////////////////////
    // Establish Connection
    mongoose.connect(DATABASE_URL);
    // Connection Events
    mongoose.connection
      .on("open", () => console.log("You are connected to MongoDB"))
      .on("close", () => console.log("You are disconnected from MongoDB"))
      .on("error", (error) => console.log(error));


    //... more code below
    
*Make sure you see the MongoDB Connection message when the server restarts*


 
