---
title: "System design"
author: "Le Chuan"
date: 2022-05-16T18:54:57+07:00
subtitle: "Design a system that scales to massive readers (10k tps)"
tags: ["fresher_2022","tech"]
---

## Requirements:
Imagine you have to design a system for serving blogs to massive readers (10k tps). How would you design the system?
## Solving:
### Step 1: Use cases and constraints:
#### Use cases:
 - Who can write a blog ? (anyone or having specific constraints) 
 - Reader searches keywords, tags,...
 - Notice to readers for new blogs.
 - ...
#### Constraints:
 - Massive readers - 10.000 transaction per second
 - Search should be fast
 - Read heavy or write heavy? Read heavy.
#### Calculate usage:
 - Size of a blog (id, text, media, ...): ~100KB
 - Number of reading requests per second: ~10000 requests
 - Number of searching requests per second: ~1000 request
 - Number of writing requests per second: ~400 request
### Step 2: Create a high level design:
{{< figure thumb="" link="/img/2.0.png" >}}
### Step 3: Design Usecase:
  - Input,Output?
  - How to store data of a usecase? (SQL or NoSQL, Object Store,Cache,...)
  - Which api,service does the use case use?
### Step 4: Scale the design:
With the increase in users or transactions, we need to scale our system. Some solution:
#### Vertical Scaling & Horizontal Scaling:
When you need to scale your system's storage power, accessibility, availability levels,... You can choose between Vertical Scaling & Horizontal Scaling.  
Simply, Horizontal Scaling is adding more machines to your system. When Vertical Scaling is making an existing machine more powerful. The Horizontal Scaling is breaking a sequential piece of logic into smaller pieces so that they can be excecuted in paralell accross multiple machines. In many respects, vertical scaling is easier because the logic really doesn’t need to change. However, the decision must be based on many other factors like *cost*, *redundancy for future*,*Regularity of Upgrades*  
{{< figure thumb="" link="/img/scaling_diff.png" >}}
#### Load balancer:
When the system has too many users, one server unit cannot meet the number of requests that are sent at the same time. You need to share your current server's work with other servers. At this point, you need a **Load balancer** to distribute it properly.  
The load balancer sends the request to the right resources and also returns the result to the appropriate clien. Hence:
- Preventing requests from going to unhealthy servers
- Preventing overloading resources
- Helping to eliminate a single point of failure
{{< figure thumb="" link="/img/load_balancer.png" >}}
#### Cache:
Cache will reduce bandwidth requirements, latency and speed up browsing, the load on your servers and database. It also improves user performance.
{{< figure thumb="" link="/img/cache.png" >}}  
  
**Besides, there are other solutions like data sharding, using CDNs,...**




