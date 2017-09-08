+++
title = "Getting Started"
date =  2017-09-08T01:42:05-04:00
weight = 5
+++

First install the Jollof global cli
```
npm i -g jollofjs
```
You also need to have mongoDB and Redis up and running.


Create your JollofJS app with:
```
jollof new myApp
```

Before you run your app, create an admin user:
```
cd myApp
jollof run createAdmin test@test.com password
```
This runs the jollof command in createAdmin.js, which exists in the commands/ directory in your project.


Now you are ready to run your jollof app:
```
npm start
```

You should now be able to see jollof running at `localhost:3001`.


At this point, if you are u for a challenge, look through and explore your project files to get a mind of how a typical JollofJS project works.