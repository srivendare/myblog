---
title: An Async Example for API request
author: "Rui"
categories:
- pandas, finance
date: 2022-09-07
---



To do multiple tasks with `async.map` *asynchronously* you have to:

1. Define a function for what you want to do with each object (your task)
2. Add that function as an event hook in your request
3. Call `async.map` on a list of all the requests / actions

Example:



```python
from requests import async
# from grequests import async

urls = [
    'http://python-requests.org',
    'http://httpbin.org',
    'http://python-guide.org',
    'http://kennethreitz.com'
]

# A simple task to do to each response object
def do_something(response):
    print response.url

# A list to hold our things to do via async
async_list = []

for u in urls:
    # The "hooks = {..." part is where you define what you want to do
    # 
    # Note the lack of parentheses following do_something, this is
    # because the response will be used as the first argument automatically
    action_item = async.get(u, hooks = {'response' : do_something})

    # Add the task to our list of things to do via async
    async_list.append(action_item)

# Do our list of things to do via async
async.map(async_list)
```

