---
title: Using Plotly Charts in Flaks
author: "Rui"
categories:
- Flask
date: 2021-09-19
---

This ariticle aims to give an idea about how to use plot.ly in Flask App.



On the route, pass json to HTML

```python
# Create a plotly chart object
fig = px.bar(industry_report , x='grade', y='num')
# Get json from the chart
figJson = json.dumps(fig, cls=plotly.utils.PlotlyJSONEncoder)
```



On the page, get json from python and create chart object

```javascript
var graphs = {{ figJson | safe }};

Plotly.plot('chart',graphs, {}); 

```

