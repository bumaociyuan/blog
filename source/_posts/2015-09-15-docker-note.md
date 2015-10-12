title: docker note
date: 2015-09-15 23:32:56
categories: docker
tags: 
---

**docker rm all non running containers**

```
$ docker rm `docker ps -aq`
```

**[Docker 加速器 2.0](https://dashboard.daocloud.io/runtimes/new)**

```
$ curl -sSL https://get.daocloud.io/daomonit/install.sh | sh -s 9ec32a679c615b0e1b72fcfb546fc8889ccfcc72

```

**加速pull**

```
$ dao pull ubuntu
```