---
title: How did I build Alippo's search from scratch? - Part 2
date: 2024-05-19T22:09:00.000Z
tags:
  - Elasticsearch
  - System design
---
In the part 1 we have seen the high level overview of how we developed the search system at alippo. About how the ingestion would work, how we will keep the data in sync between main DB and Elasticsearch cluster. If you haven't seen it yet please check it out [here](https://sumittiware.dev/post/how-did-i-build-alippos-search-from-scratch-part-1/).

In this article we will look into what design choices we made to achieve the system we are looking for. We tried lot of platforms how has already cracked there search system like Udemy, Swiggy, Zomato to develop our system just like them.

Before we start building the product our first focus was to have a clear understanding of how the user flow would look like how will we show the search suggestions based on the query? What will be the will be the action when user clicks one of the suggestion? Once this understanding was clear we can develop the api's and system around the same.

What we need to build was : 

1. **Content type suggestions:** We need to show the suggestion to used on all the content types that we have in our system like Category, Course, Instructors. 

2. **Unified Search result page:** This involves understanding how will we render all the types on the responses on the single screen.



\    One fun fact was that, when I was researching and reading various tech blogs I found LinkedIn's tech blog where they mentioned that they had to create a new more generic search component to support all the various search type so as to reduce the time for a new search entity to the end user which was from 15 days to 1 month in case LinkedIn. But I realised that was never the issue in out case since we already have out own DLS(design language system) to render the BE controlled UI to the mobile app adding new search entity in the result was simple just add the select the type of component you want to render for a particular type and return it. I can talk about how we developed DLS in any other blog.

   Now when we were brain storming to support multiple content type there was a discussion weather to store the different content type data in the seperate index and while querying we would have to fire the query to all the indices and make the final result based on the response of each query.

   Or we had another approch was to keep a global index that will have all the content types and the along with the there title, description and dump of the other fields for the full text search. Then we can just render all the content types in the search suggestion then for the final search suggestion we would one render final seachearchable entity which was courses in our case, see the diagram for the better understaning.

   So the above approch reduced our need to query in multiple index at the same time and supported the multiple content type using single index in suggestion now for the search result we can pass the final entitiy type like course, categroy, instructor in out case and the server will enrich the results data based in the index of that content type.

   But this added one more over head now we had to maintain the consistency between different indices suppose something changed in the course we need to update the course index and then the global index at the same time.

To achive this we made some changes in our ingester server (discussed in the last blog) where we allowed each of the content type entity to decalre it's dependent entity so that once the changes are made in course it will fire a update event for globalindex and update will be made in the correspnding index.
