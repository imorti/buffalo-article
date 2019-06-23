# Overview
This article is a walk through of basics for developing with the Gobuffalo.io framework. 

## Assumptions
* gobufalo installed successfully
* you're run `buffalo plugins list` and seen `buffalo pop` is installed
* go version go1.11.5 darwin/amd64 (running on MAC OSX)
* Buffalo version is: v0.14.6 
  

# Set up and run locally
1. Run `buffalo new <app name> --db-type=<db name>`. 
2. Open `<app name>` directory in favorite editor.
3. Open `database.yml` in your editor. 
4. Modify settings to match authentication, port and database schema requirements for `dev` and `test`. 
5. Run `buffalo db create`. This will create the database for you locally. 
6. With this successfully run, I recommend `git add && git commit -m "init commit"`. 
7. Ok, now run `buffalo dev`. 
8. Open `http://localhost:3000` to view app succesfully running. You should see the `routes` page listing currently specified routes. 
   
At this point you have a running `gobuffalo` application running locally. 

# Next: entities, attributes and persistence. 
Now let's modify our application to add CRUD operations for an entity. 

1. Run `buffalo g resource <resource name>` (could be users etc.).
    * notice how it creates migrations, actions, models and templates. 
    * Example: `buffalo generate resource widget title description:nulls.Text` will generate migrations, actions, models and templates plus attributes. 
2. Run `buffalo db migrate up`. This will modify the database. 
3. Restart your application. (kill process then run `buffalo dev`)
4. Now, test your new resource by opening `http://localhost:3000/<resource name>/` (<http://localhost:3000/widgets/> will show the index page for widgets)
5. Create a new `<resource name>` or `widget` to test persistence. If successful, you're off to the races! Be sure to commit changes and push. 