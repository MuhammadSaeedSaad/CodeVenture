# Elasticsearch

## basics

## basic CRUD operatiosn
```java
// Get info about cluster healths
GET _cluster/health

// Get info about nodes in a clusters
GET _nodes/stats

// create an index
PUT favorite_candy

// indexing (creating or putting in an index) a document can be done using POST or PUT
// using POST >> id is auto-generated
POST favorite_candy/_doc
{
  "first_name": "Lisa",
  "candy": "Sour Skittles"
}

// using PUT the id is defined by the user
PUT favorite_candy/_doc/1
{
  "first_name": "John",
  "candy": "Starburst"
}

// PUT will overwrite existing document .. avoid that using create endpoint
// this will cause an error
PUT favorite_candy/_create/1
{
  "first_name": "Finn",
  "candy": "Jolly Ranchers"
}

PUT favorite_candy/_create/2
{
  "first_name": "Mohamed",
  "candy": "Helw"
}

// read single document by its id
GET favorite_candy/_doc/1

// update a document
POST favorite_candy/_update/1
{
  "doc": {
    "candy": "M&M's"
  }
}

// make sure that the field has changed
GET favorite_candy/_doc/1

// delete a document
DELETE favorite_candy/_doc/2
```


## Questions
1. Why used the "query" again inside the clause of "headline" ?
```java
GET news_headlines/_search
{
  "query": {
    "match_phrase": {
      "headline": {
        "query": "Shape of You"
      }
    }
  }
}

A: we can get rid of the second "query" and the request will be ok.
```