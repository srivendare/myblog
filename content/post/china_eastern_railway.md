---
title: Organizing Geospatial Data case study on China Eastern Railway
author: "Rui"
categories:
- Map
- Ditushu
- NLP
date: 2023-05-16
---



This article is about some random outcomes for organizing info in a Multi Language Maps.



The Original Map Image is in both Russian and Traditional Chinese:

![img](https://pic.baike.soso.com/ugc/baikepic2/16500/cut-20220107211128-1527755848_jpg_938_625_129642.jpg/1284)



After OCR through free version web tools:

| ID   | English Name | Chinese Name | Russian Name | Longitude  | Latitude  | Country Belonged To | Year of Train Station Built |
| ---- | ------------ | ------------ | ------------ | ---------- | --------- | ------------------- | --------------------------- |
| 1    | Changchun    | 长春         | Чанчунь      | 125.323544 | 43.817071 | China               | 1898                        |
| 2    | Shenyang     | 沈阳         | Шэньян       | 123.431472 | 41.805698 | China               | 189                         |
| 3    | Tianjin      | 天津         | Тяньцзинь    | 117.199500 | 39.085097 | China               | 1888                        |



After Cleaning to Json Format:

```python
[
  {
    "_id": 13,
    "title": "长春",
    "location": {
      "type": "Point",
      "coordinates": [
        125.323544,
        43.817071
      ]
    }
  },
  {
    "_id": 14,
    "title": "沈阳",
    "location": {
      "type": "Point",
      "coordinates": [
        123.431472,
        41.805698
      ]
    }
  },
  {
    "_id": 15,
    "title": "天津",
    "location": {
      "type": "Point",
      "coordinates": [
        117.1995,
        39.085097
      ]
    }
  },
  {
    "_id": 16,
    "title": "北京",
    "location": {
      "type": "Point",
      "coordinates": [
        116.407396,
        39.9042
      ]
    }
  },
  {
    "_id": 17,
    "title": "鞍山",
    "location": {
      "type": "Point",
      "coordinates": [
        122.994646,
        41.108546
      ]
    }
  },
  {
    "_id": 18,
    "title": "大连",
    "location": {
      "type": "Point",
      "coordinates": [
        121.614682,
        38.913689
      ]
    }
  },
  {
    "_id": 19,
    "title": "元山",
    "location": {
      "type": "Point",
      "coordinates": [
        125.754249,
        39.160949
      ]
    }
  }
]

```

