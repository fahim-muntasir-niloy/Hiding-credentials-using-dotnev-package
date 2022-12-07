# Hiding-credentials-using-dotnev-package

In the backend, we don't want any of the important information to be left open. `MongoDB` URL, id passwords etc are such items that has to be kept secretly, so that they don't get published in GITHUB or anywhere.

## Step 1
Install `npm` in the project.

```terminal
npm init -y
```

## Step 2
In project, install `dotenv` package from `npm`

```terminal
npm install dotenv --save
```

## Step 3
Create a `.env` file in the project folder. This environment file will contain all the credentials. The file will look like this:

``` js
USER_NAME='FAHIM MUNTASIR'
USER_PASS=12345
MONGODB_URL='mongodb+srv://fahimMuntasir:retryWrites=true&w=majority'
```

## Step 4
> This is a very crucial step.

Now add a `.gitignore` file in your project. The files selected here are left while uploading code to GITHUB. We don't want these files to be seen from outside.

```
\node_modules  
.env  
package.json
```


### Environment setup is done. To use this values in anywhere of the project file use following steps.

## Step 5
Create a `js` file and require `dotenv` package.

``` js
// requiring dotenv as variable
let env = require('dotenv').config()  

// for using mongodb
let mongoClient = require('mongodb').MongoClient
```

## Step 6
Any environment variable is called as a `process`. Let's say, we want the MONGODB_URL in the project. This will be called as:

```js
// Calling URL
let mongoDbURL = process.env.MONGODB_URL

// New connection to the url server
let client = new mongoClient(mongoDbURL)
```

In This way, we used the data from the secret environment file, without disclosing them using `dotenv` package.
