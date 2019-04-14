# ELK Stack Using Docker Compose

The Elastic stack version **7.0.0** using Docker Compose and the official (OSS) images from Elastic:
- https://github.com/elastic/elasticsearch-docker
- https://github.com/elastic/logstash-docker
- https://github.com/elastic/kibana-docker


See https://www.elastic.co/blog/elastic-stack-7-0-0-released for more info about the features of 7.0.0.


## What's in the box?

A `docker-compose.yml` file, defining:
 - 2 Elasticsearch master nodes
 - 1 Elasticsearch slave (data/ingest) node
 - Logstash
 - Kibana

Configuration files for each type of service.


## Usage

Clone this repo and run `docker-compose up`. Watch it unfold, and hopefully you
should be able to access the cluster at localhost:5601 through Kibana.


## Scaling

Seems to be a bit shaky, but you should be able to scale the slave (data, ingest) nodes using `docker-compose scale`. For example, if you want 3 slave nodes, write `docker-compose scale elasticslave=3`.

I have yet to find an easy way to scale the master nodes using Docker Compose without everything breaking.


# Other Projects

This project is by far the only one to attempt a Docker Compose setup for the
Elastic stack. Here are a few notewothy projects:

- https://github.com/deviantony/docker-elk Is excellent and very well documented. It is easy to get started and configure/scale, but it does not yet work on ELK version 7.0.0.

- https://github.com/spujadas/elk-docker Works with ELK 7.0.0, but by default runs everything inside a single Docker container from a customly built image. Documentation is thorough.


Thus this project was made. I wanted my images to be as close to the official builds as possible, and make it easy to scale using docker-compose.  I find it to fit neatly between the two projects.  But there is no documentation. Can't have it all, now can we?
