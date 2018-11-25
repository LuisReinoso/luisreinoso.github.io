---
layout: post
title: "Consume a Github api in javascript using sailsjs"
description: "Use sailjs to provide an api to consume another api"
categories: [sails]
tags: [sails, sailsjs, fetch]
---

This is a solution for a little test that I do.

Install a sailsjs api

{% highlight bash %}
npm install -g sails
{% endhighlight %}

Create a new project. Choose an Empty Sails app

{% highlight bash %}
sails new 
{% endhighlight %}

Create a simple action2

{% highlight bash %}
sails generate action getApi
{% endhighlight %}

Edit `config/routes.js` add new route below of api endpoints.
{% highlight javascript %}
'GET /getApi' : {action: 'get-api'}
{% endhighlight %}

To verify it's all is ok.. start application, 

{% highlight bash %}
sails lift
{% endhighlight %}

Open the web browser and on url bar type localhost:1337/getApi. Then you will see an ok.

Install node-fetch to use fetch and get the result of Github api.

{% highlight bash %}
npm install --save node-fetch
{% endhighlight %}

Edit `api/controllers/get-api`

{% highlight javascript linenos %}
const fetch = require('node-fetch');

module.exports = {
  friendlyName: 'Get api',

  description: '',

  inputs: {},

  exits: {},

  fn: async function(inputs, exits) {
    fetch('https://api.github.com/users/luisreinoso/repos')
      .then(apiRes => apiRes.json()) // parse Response to json
      .then(repos => {
        let nameRepos = [];
        repos.forEach(repo => nameRepos.push(repo.name));
        sails.log.info(nameRepos);
        return exits.success({ nameRepos: nameRepos });
      })
      .catch(error => {
        sails.log.error(error);
        return exits.serverError();
      });
  }
};
{% endhighlight %}

To verify it's all is ok.. re-start application, 

{% highlight bash %}
sails lift
{% endhighlight %}

Open the web browser and on url bar type localhost:1337/getApi. Then you will see my repos name.

**Notes**
* fetch is not in node by default
* sails has simple controllers and actions2 to write the api logic

**References**
* https://www.npmjs.com/package/node-fetch