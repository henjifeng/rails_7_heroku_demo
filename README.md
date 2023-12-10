# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

new postrgres docker
```
docker network create app
docker run --name postgres -e POSTGRES_PASSWORD=123123 -e POSTGRES_USER=postgres --network app -p 5432:5432 -v /home/jack/postgres_db:/var/lib/postgresql/data -d postgres
```



