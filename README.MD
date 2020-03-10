# Overview

This is an example of a full stack application: Front End, Server Side REST API, and a Data Store.  It is based off of Angular's Tour of Heroes.

This example is incomplete on purpose to allow for learners to fill in the necessary components.

# Componets

 * Server Side Data Store
 * Server Side REST API
 * Front End GUI

## Server Side Data Store
This is the mechanism for storing the Heroes database.

Initially, this will be set up as an Elasticsearch 6.4 data store for local instantiation.  However, alternate solutions (Amazon S3 buckets, PostGRES, MongoDB, and others) are possible.

## Server Side REST API
This is the mechanism that will handle requests from the front end GUI and interact with the Data Store.

Initially, the service endpoints will be defined in a Swagger definitions file and used to generate GOLANG code stubs for development.  However, other RESTful service definitions are possible and other programming languages could be used instead.

Initially, this is the target component for learning.  The setup will be left incomplete for the learning developer to fill in here.

## Front End GUI
This is the mechanism for user interaction.

This is a modified copy of Angular's Tour of Heroes: Part 6 (https://angular.io/tutorial/toh-pt6).  With the main modification being the omission of the InMemoryDbService.  Instead, the Hero Service (and other DB API calls) are configured to point to the REST API.