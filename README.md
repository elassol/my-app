## Building it
``npm install``


## Usage Rem calculator

p {
   @include font-size(14px)
}

## OUTPUT REM MIXING

p {
 font-size: 14px; //Will be overridden if browser supports rem
font-size: 0.8rem;
}


## Building it
``npm install``

## Starting the app
``PORT=4321 node app.js``

## Create a campaign
gulp new --name campaign_name || gulp new --name campaign_name --watch true
(--watch true flag starts a gulp watch, see below)

## Compile JS & CSS
gulp
Compiles JS & Less => CSS
gulp watch
Watch for changes and compile JS and Less => CSS

## Delete a campaign
gulp delete --name campaign_name

## Show routes
gulp routes
Lists all project routes
Or see here:
localhost:[PORT]/routes

## Images in HTML
Use absolute paths and ftp images to the server.
or
Use relative paths with the assetUrl option:
src=assetUrl("local/path")
and run the app with the following command to generate absolute paths in the browser
ASSET_URL=https://s3-eu-west-1.amazonaws.com/noths-prod-eu-west-1-campaigns/campaigns/ PORT=3000 node app.js

## Images in JS and CSS
Use relative paths. All images, JS and CSS will sit relatively on the file system.

## Release to production or QA
FTP your campaigns images, JS file and CSS file from ./public to
http://emails.noths.com/emails/campaigns/[year]/[project]/
Where year = current year and project = campaign name
(Get access from devops)

login to admin page of NOTHS site or QA site and create a new page.

Add this template to page:

## Production page template

<link rel="stylesheet" href="https://s3-eu-west-1.amazonaws.com/noths-prod-eu-west-1-campaigns/campaigns/styles/[filename].css">

[HTML MARK UP HERE]

<script>
  jQuery(document).ready(function() {

    require.config({
        paths: {
          'campaign': "https://s3-eu-west-1.amazonaws.com/noths-prod-eu-west-1-campaigns/campaigns/scripts/[filename]"
        }
    });

    require(['campaign']);

  });
</script>

## Production page template end

Copy your project's html from your local browsers inspector

Tabify the HTML here:
http://tools.arantius.com/tabifier

Paste new tabified HTML into the template above.

## Minify images
gulp images
Minify your images before going to production

## Data Storage
Use Bronto
http://bronto.com/
or Firebase
https://www.firebase.com/
Details to come...
