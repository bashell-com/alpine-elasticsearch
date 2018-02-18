Elasticsearch on Alpine Linux Docker Image
==========================================

This image provides Elasticsearch based on Alpine Linux latest stable
version.  All files are adapted from the official Elasticsearch docker
repository.

Supported tags and respective Dockerfile links
----------------------------------------------

-   `latest` ([Dockerfile](https://bitbucket.org/bashell-com/alpine-elasticsearch/src/tip/Dockerfile?fileviewer=file-view-default))
-   `5.6.7` ([Dockerfile](https://bitbucket.org/bashell-com/alpine-elasticsearch/src/5.6.7/Dockerfile?fileviewer=file-view-default))
-   `2.4.6` ([Dockerfile](https://bitbucket.org/bashell-com/alpine-elasticsearch/src/2.4.6/Dockerfile?fileviewer=file-view-default))

Prerequisite
------------

For image `5.6.7` or newer, `vm.max_map_count` must set to
**262144** on the host that run this image.

    $ sudo sysctl -w vm.max_map_count=262144

How to use this image
---------------------

You can run the default elasticsearch command simply:

    $ docker run -d bashell/alpine-elasticsearch

You can also pass in additional flags to elasticsearch:

    $ docker run -d bashell/alpine-elasticsearch \
      elasticsearch -Des.node.name="TestNode"

This image comes with a default set of configuration files for elasticsearch,
but if you want to provide your own set of configuration files, you can do so
via a volume mounted at `/opt/elasticsearch/config`:

    $ docker run -d \
      -v "$PWD/config":/opt/elasticsearch/config \
      bashell/alpine-elasticsearch

This image is configured with a volume at `/opt/elasticsearch/data` to hold the
persisted index data. Use that path if you would like to keep the data in a
mounted volume:

    $ docker run -d \
      -v "$PWD/esdata":/opt/elasticsearch/data \
      bashell/alpine-elasticsearch

This image includes `EXPOSE 9200 9300`
([default http port](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-http.html)),
so standard container linking will make it automatically available to the
linked containers.

Issues
------

If you have any problems with or questions about this image, please contact us
through a [Bitbucket issue](https://bitbucket.org/bashell-com/alpine-elasticsearch/issues).

