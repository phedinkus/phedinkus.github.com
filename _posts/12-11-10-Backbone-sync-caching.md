---
layout: post
title: Backbone.sync, Amplify.js and caching
published: false
---

During devlopment of an application using [Chaplin](https://github.com/chaplinjs/chaplin)/[Backbone](http://documentcloud.github.com/backbone/), our team realized we had a high number of HTTP requests for the same resource at the same time. The root cause was the way we had utilized the app architecture in Chaplin. Each routing change fires off a controller action which in turn instantiates a view and the view's model or collection. The controllers are sandboxed so each instance of model or collection needed to be isolated since it was broken down on routing changes. We discussed a number of options for caching between calls. I set off to research caching the response from the server in localstorage.

Over-writing the sync method is encourged in Backbone.js's docs as a logical place to customize storing data.

> The sync function may be overriden globally as Backbone.sync, or at a finer-grained level, by adding a sync function
> to a Backbone collection or to an individual model.
>
> <small>from Backbone.sync documentation</small>

Looking for examples leads to numerous drop-in adapters for Backbone.sync. One of the most common examples is [Backbone.localStorage](https://github.com/jeromegn/Backbone.localStorage). This adapter is a replacement for remote data storage and since I still wanted to save to a db, this adapter isn't a good fit for caching.

[Backbone.dualStorage](https://github.com/lucian1900/Backbone.dualStorage) looked promising. At first glance it does everything we needed

I had recently read an article about [amplify.js](http://amplifyjs.com/) and pondered the idea of what in-browser caching might look like using localstorage. Off I went to play!
####Caching Techniques

I spent some time reading about caching and different techniques. Two in particular seemed like a good fit for the task at hand -- write-through caching and key-value 

**Write-through cache**

Questions that arise:
  How to invalidate the cache
  What if the cache becomes out of sync with the remote data - how do you ensure it's accurate
  Provide a way for other collections to check if a call is in transit to the same url.