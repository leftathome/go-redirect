go-redirect [![Docker Build Status](https://img.shields.io/docker/build/scottmiller171/ssl-redirect.svg)]()
===========

[![Join the chat at https://gitter.im/smiller171/go-redirect](https://badges.gitter.im/smiller171/go-redirect.svg)](https://gitter.im/smiller171/go-redirect?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Redirect HTTP to HTTPS with Docker

[![](https://images.microbadger.com/badges/version/scottmiller171/ssl-redirect.svg)](https://microbadger.com/images/scottmiller171/ssl-redirect "Get your own version badge on microbadger.com")  
[Docker Hub](https://hub.docker.com/r/scottmiller171/ssl-redirect/)
# Supported Tags and `Dockerfile` links
* `latest` [(Dockerfile)](https://github.com/smiller171/go-redirect/blob/master/Dockerfile) - [![](https://images.microbadger.com/badges/image/scottmiller171/ssl-redirect.svg)](https://microbadger.com/images/scottmiller171/ssl-redirect "Get your own image badge on microbadger.com")
* `1.3` [(Dockerfile)](https://github.com/smiller171/go-redirect/blob/1.3/Dockerfile) - [![](https://badge.imagelayers.io/scottmiller171/ssl-redirect:1.3.svg)](https://imagelayers.io/?images=scottmiller171/ssl-redirect:1.2 'Get your own badge on imagelayers.io')
* `1.2` [(Dockerfile)](https://github.com/smiller171/go-redirect/blob/1.2/Dockerfile) - [![](https://badge.imagelayers.io/scottmiller171/ssl-redirect:1.2.svg)](https://imagelayers.io/?images=scottmiller171/ssl-redirect:1.2 'Get your own badge on imagelayers.io')
* `1.1` [(Dockerfile)](https://github.com/smiller171/go-redirect/blob/1.1/Dockerfile) - [![](https://badge.imagelayers.io/scottmiller171/ssl-redirect:1.1.svg)](https://imagelayers.io/?images=scottmiller171/ssl-redirect:1.1 'Get your own badge on imagelayers.io')
* `1.0` [(Dockerfile)](https://github.com/smiller171/go-redirect/blob/1.0/Dockerfile) - [![](https://badge.imagelayers.io/scottmiller171/ssl-redirect:1.0.svg)](https://imagelayers.io/?images=scottmiller171/ssl-redirect:1.0 'Get your own badge on imagelayers.io')

# What is this?
This image accepts any http request and redirects to the https version of the same page.  
It does not serve any pages.

# What is this for?
The primary reason for this image is for doing SSL termination on a load balancer (eg: AWS ELB) in the simplest possible way.

# How do I use it?
* Run this image on any TCP port, and your own web server image on another.
```bash
docker run -d -p 8080:80 scottmiller171/ssl-redirect
docker run -d -p 80:80 my-web-server-image
```
* Forward HTTP 80 on your load balancer to whatever port this image is running on.
* Forward HTTPS 443 on your load balancer to whatever port your own web server is running on.

All HTTP requests will hit this image and be redirected to make HTTPS request. This is abstracted from the user.

# How do I build it myself?

```sh
docker build -t ssl-redirect .
docker run ssl-redirect
```
