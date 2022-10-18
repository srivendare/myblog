---
title: Using Plotly Charts in Flaks
author: "Rui"
categories:
- Flask
date: 2021-09-19
---

This ariticle aims to give an idea about how to use plot.ly in Flask App.

On the route

```
# Create a plotly chart object
fig = px.bar(industry_report , x='grade', y='num')
# Get json from the chart
figJson = json.dumps(fig, cls=plotly.utils.PlotlyJSONEncoder)
```

On the page

```
var graphs = {{ figJson | safe }};

Plotly.plot('chart',graphs, {}); 

```

[^1]: Test Footnote
[^2]: Test Footnote2
