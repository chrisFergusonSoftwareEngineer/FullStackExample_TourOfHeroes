# Introduction

This is the mechanism for storing the Heroes database.

Initially, this will be set up as an Elasticsearch 6.4 data store for local instantiation.  However, alternate solutions (Amazon S3 buckets, PostGRES, MongoDB, and others) are possible.

# Developer Setup

## Prerequsites

1. Docker: https://docs.docker.com/install/
2. Docker Elasticsearch: `docker pull docker.elastic.co/elasticsearch/elasticsearch:6.4.3`
    a. Note: for this tutorial we are using ElasticSearch 6.4.  Any 6.X version should work without modification  However, changing the Major version of ES (7.X, 8.X, 2.X, etc) would necessitate a change inthe Server Side REST API to use the corresponding ElasticSearch library.
    b. Start the ES image: `docker run -d --name "ES_Heroes" -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:6.4.3`
    c. Note: Once this setup is complete, the developer is expected to handle management of the Container (starting, stopping, removing, re-running) on their own.  Further instruction on Docker container management is not included here.

## Setup
1. With the ES Container running, execute the following command: `curl -H "Content-Type: application/json" --data-binary @TourOfHeroesDataPrimer.json http://localhost:9200/system_availability_metrics_2020-02-12/_doc/_bulk`
    a. Note: You may need to update the exact path to the file in the --data-binary option to match your local filesystem.

## Reviewing the Data
Use the following commands at your discretion to review the data loaded in the database at any time it is running.
Note, you may use the URLs below in Postman as an alternative to curl.

* Check the indices: `curl localhost:9200/_cat/indices?v`
* Fetch 10 items from the database: `curl localhost:9200/heroes/_search?pretty`
* Fetch a specific entry by ID field: `curl "localhost:9200/heroes/_search?pretty&q=id:17"`
    - Note the quotes (`""`) around the URL, this is necessary to avoid confusing the terminal.