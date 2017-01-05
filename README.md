Links:

Meteor hosted
Heroku hosted
Functionality:

Create / Change / Remove nodes
Create / Change / Remove relationships
Graph visualization (by visjs)
Latency compensation (on visjs level, but we wait for server response)
Client synchronization with minimal delay
Exception-less conflicts UX-workflow
Both examples powered by GrapheneDB
Set up Neo4j

Locally:

Download Neo4j
In Terminal go to downloads folder and type tar -xf <downloaded filename> -C ~/neo4j/
Start Neo4j: ~/neo4j/bin/neo4j start
Go to localhost:7474 and set up new credentials
Go to server/main.coffee, change credentials to your instance of Neo4j
Further reading
GrapheneDB:

Go to GrapheneDB, create an account and free (or paid) plan DB
Get DB's credentials from "DATABASES" > "Connection" tab
Go to server/main.coffee, change credentials to your instance of Neo4j
Heroku GrapheneDB Add-on:

From dashboard go to your app
On "Resouces" tab type in "Add-ons" section: graphenedb
Select plan and proceed through further steps
Get DB's credentials
Go to server/main.coffee, change credentials to your instance of Neo4j
Deploy to Meteor

Set up Neo4j - see sections above
From Meteor's application directory run:
meteor deploy <your-app-name>.meteor.com
Deploy to Heroku

Go to Heroku create and confirm your new account
Go though Node.js Tutorial
Install Heroku Toolbet
Set up Neo4j - see sections above
Then go to Terminal into Meteor's project directory and run:
meteor build ../build-<your-app-name>
cd ../build-<your-app-name>
tar xvzf <name-of-archive> -C ./
cd bundle/
cp -Rf * ../
cd ../
rm -Rf bundle/
rm -Rf <name-of-archive>
git init 
git add .
nano Procfile
web: node main.js
# press ctrl + o
# press Enter (return)
# press ctrl + x
npm init
# go though all steps by pressing Enter (return)
npm install fibers@1.0.7 mailcomposer progress http-proxy sockjs keypress stream-buffers simplesmtp request useragent clean-css uglify-js mongodb handlebars semver mime nib stylus less coffee-script optimist gzippo connect
# Ignore all warnings (but not errors)
heroku create <your-app-name> --buildpack https://github.com/heroku/heroku-buildpack-nodejs
# This command will output something like: https://<your-app-name>.herokuapp.com/ | https://git.heroku.com/<your-app-name>.git
# Copy this: `http://<your-app-name>.herokuapp.com`, note use only `http://` protocol!
heroku config:set ROOT_URL=http://<your-app-name>.herokuapp.com
git commit -m "initial"
git push heroku master
Go to http://<your-app-name>.herokuapp.com
If you app has errors:
Check logs: heroku logs --tail
Try to run locally and debug: heroku run node