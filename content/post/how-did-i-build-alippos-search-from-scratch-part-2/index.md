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

1. **Content type suggestions**: We need to show the suggestion to used on all the content types that we have in our system like Category, Course, Instructors. 

2. **Unified Search result page**: This involves understanding how will we render all the types on the responses on the single screen.

   One fun fact was that, when I was researching and reading various tech blogs I found LinkedIn's tech blog where they mentioned that they had to create a new more generic search component to support all the various search type so as to reduce the time for a new search entity to the end user which was from 15 days to 1 month in case LinkedIn. But I realised that was never the issue in out case since we already have out own DLS(design language system) to render the BE controlled UI to the mobile app adding new search entity in the result was simple just add the select the type of component you want to render for a particular type and return it. I can talk about how we developed DLS in any other blog.\
\
Now when we were brain storming for the
