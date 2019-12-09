---
layout: post
title:      "Where and How to store API Keys in your React Application"
date:       2019-12-09 00:10:40 +0000
permalink:  where_and_how_to_store_api_keys_in_your_react_application
---


In this article, I want to write how to store and hide your important variable such as API keys in a React Application.

An API key is just a string but a secret token for your application to contact the verification server.
We don’t want to show the important identifier - API Key and shouldn’t store it on Git repositories. Such sensitive information should be stored in a safe place.

## Where should I save my API Keys in a React Applicaton ?
The easiest way for me is storing API Keys in the environment file.
Environment file (`.env`) is a configuration text file that is used to define variables. You can pass this variable in your applications - other directories.

### Create `.env` file
1. Create a `.env` file in the root directly in your React Application.
2. If you already pushed your application to the GitHub, you should have `.gitignore` file. In this file, please add/write `.env`. In this way, `.env` file will be ignored in all of your GitHub repositories. 
3. Store API Keys in `.env` file.
Copy the API Keys from the site you access and paste the keys in the variable. For example,<br>
`REACT_APP_APIKEY=abcde1234XXXXXXXXXXXXXXYYYYYZZZ`

**Please maks sure the variable name starting with `REACT_APP` in your React Application. You can name anything after the `REACT_APP`. I simply use `APIKEY` in this example.

### Install dotenv npm package
We need dotenv npm package to access this environment variable.

##### What is `dotenv`?
According to npm 
> Dotenv is a zero-dependency module that loads environment variables from a `.env` file into `process.env`. 

[dotenv](https://www.npmjs.com/package/dotenv)

1. Install `dotenv npm` package.<br>
In your terminal, please type: <br>
`npm install dotenv`

2. Now You can access the environment variable in your files by:<br>
`process.env.REACT_APP_APIKEY`  

3. Store the env variable in your directory and use it when you have an HTTP request like this.<br>
```
const API_KEY = process.env.REACT_APP_APIKEY 
fetch(`http://www.api.SOME-API.com/information?apiKey=${API_KEY}`)
```

<div style="margin-top: 5%;">
You should be able to access the data successfully now without displaying your API Key ! 

There are another ways to store API Keys. But I think it is easier way to store it.<br>
Thank you!
</div>





 






