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

At alippo anything we build we have a philosophy that we don't have to do everything from scratch, there are already a lot of brilliant people how already solved that we are trying to solve, so just try to make the best use of the available opensource projects to build out system, same with the search.\
\
In this series of article I will walk you through how we build Alippo's search system.

While building this first question that comes in the mind is which DB to use since our Posgresql is general-purpose databases primarily designed for efficient storage, retrieval, and management of structured or semi-structured data, rather than full-text search operations. While they may offer basic full-text search capabilities, they lack the specialised indexing, ranking algorithms, and performance optimizations required for complex search queries and large-scale search applications. That why we used Elastisticsearch.
