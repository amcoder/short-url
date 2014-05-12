# Short Url

## Overview

Short Url is a project specification that can be used to help evaluate different
languages and frameworks.

## Implementations

The currently implemented versions are:

- [Rails][rails-short-url]: A standard rails project.

## Specification

A short url application provides shortened urls to replace longer ones.

### Web Application

The web application provides the user interface to allow one to shorten a url
by hand. The user interface should provide a page allowing the user to enter the
full url into a form. When submitted, the system will generate a short url, save
the information in the datastore, and display a new page to the user with the
short version of the url.

When the user goes to the short version of a url, the system will redirect the
user to the original full url, as well as save statistics about the redirect
to the datastore.

The application will also provide a page that will display statistics about a
short url. Possible statistics to include are:

- Number of requests
- Top referrers
- Graphs

### API

The application must provide a web-based API endpoint to allow programmatic
creation and querying of short urls. The API should conform to the idiomatic
style of API design for the given framework.

An example REST-based API might look like:

POST /
  post data: { url: [full url] }
  response: { short-url: [shortened url] }
Create a new short URL.

GET /[code]
  response: { url: [full url] }
Get the full url given a code. This does not store redirect statistics about the
request.

### Testing

Each implementation must have complete tests including unit and acceptance tests.

[rails-short-url]: http://github.com/amcoder/rails-short-url
