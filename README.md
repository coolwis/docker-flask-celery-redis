[![Build Status](https://travis-ci.org/dlesz/docker-flask-celery-redis-hotcode.svg?branch=master)](https://travis-ci.org/dlesz/docker-flask-celery-redis-hotcode)

# origin git url 
```bash
https://github.com/mattkohl/docker-flask-celery-redis
```

# Docker Flask Celery Redis

A basic [Docker Compose](https://docs.docker.com/compose/) template for orchestrating a [Flask](http://flask.pocoo.org/) application & a [Celery](http://www.celeryproject.org/) queue with [Redis](https://redis.io/)

### Installation

```bash
# git clone https://github.com/mattkohl/docker-flask-celery-redis   ( origin code url )
# git clone https://github.com/coolwis/docker-flask-celery-redis
```

### Build & Launch

```bash
docker-compose up -d --build
```

### Enable hot code reload

```
docker-compose -f docker-compose.yml -f docker-compose.development.yml up --build

# docker-compose.development.yml 에러발생하여  uwsgi 모듈로 변경함
```

This will expose the Flask application's endpoints on port `5001` as well as a [Flower](https://github.com/mher/flower) server for monitoring workers on port `5555`

To add more workers:
```bash
docker-compose up -d --scale worker=5 --no-recreate
```

To shut down:

```bash
docker-compose down
```


To change the endpoints, update the code in [api/app.py](api/app.py)

Task changes should happen in [queue/tasks.py](celery-queue/tasks.py) 

---

adapted from [https://github.com/itsrifat/flask-celery-docker-scale](https://github.com/itsrifat/flask-celery-docker-scale)
