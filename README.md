# Docker secured Apache2 with secure SSL (peotidbit/hoolmgreen-apache2)
_maintained by Peotidbit-Hoolmgreen_

## What is it

This Dockerfile (available as ___peotidbit/hoolmgreen-apache2___) gives you a ready to use secured production apache2 server.

## Environment variables and defaults

#* __HSTS\_HEADERS\_ENABLE__
# * default: not set - if set to any value the HTTP Strict Transport Security will be activated on SSL Channel
#* __HSTS\_HEADERS\_ENABLE\_NO\_SUBDOMAINS__
# * default: not set - if set together with __HSTS\_HEADERS\_ENABLE__ and set to any value the HTTP Strict Transport Security will be deactivated on subdomains


## Running peotidbit/hoolmgreen-apache2 Container

This Dockerfile is not really made for direct usage. It should be used as base-image for your apache2 project. But you can run it anyways.

You should overwrite the _/etc/apache2/external/_ with a folder, containing your apache2 __\*.conf__ files (VirtualHosts etc.), certs and a __dh.pem__.   
_If you forget the dh.pem file, it will be created at the first start - but this can/will take a long time!_

    docker run -d \
    -p 80:80 -p 443:443 \
    -v /home/peotidbit/certificates:/etc/apache2/external/ \
	-v /home/peotidbit/docker/hoolmgreen-data/public-html:/var/www/html \
    peotidbit/hoolmgreen-apache2

## Based on

This Dockerfile is based on the [/_/ubuntu:16.04/](https://registry.hub.docker.com/_/ubuntu/) Official Image.

