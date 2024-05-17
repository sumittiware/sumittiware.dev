---
title: How did I build Alippo's search from scratch? - Part 1
description: ""
date: 2023-05-10
updated: 2023-05-10
draft: true
slug: alippo-search-from-scratch
tags:
  - "Search "
  - Search system
  - Elasticsearch
---
Search systems play a key role in most of the systems as it allows user to find given product in efficient manner. In Alippo we had around 2K courses among which users comes to our app and pick the course based on there interest. So the need of the search system is must.

At alippo anything we build we have a philosophy that we don't have to do everything from scratch, there are aready a lot of brilliant people how already solved that we are trying to solve, so just try to make the best use of the available opensource projects to build out system, same with the search.\
\
In this series of article I will walk you through how we build Alippo's search system using. 

***No system design is perfect, everything comes with pros and cons.***
