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

> [DHH Rails 7 DEMO with HERO KU](https://www.youtube.com/watch?v=mpWFrUwAN88)

> [Deploying Ruby on Rails to Heroku](https://www.youtube.com/watch?v=ONsUBM10ypg)

> [ruby heroku官网参考](https://devcenter.heroku.com/articles/getting-started-with-ruby#use-a-database)

> [Rails heroku 官网参考教程](https://devcenter.heroku.com/articles/getting-started-with-rails7#local-setup)

```
#增加插件数据库
heroku addons:create heroku-postgresql:mini

# heroku addons:docs heroku-postgresql

#配置DATABASE 等环境变量
heroku config:set TIMES=10
```


删除heroku 项目和插件
```
heroku addons:destroy heroku-postgresql
 ▸    WARNING: Destructive Action
 ▸    This command will affect the app polar-eyrie-78321
 ▸    To proceed, type polar-eyrie-78321 or re-run this command with
 ▸    --confirm polar-eyrie-78321

> --confirm polar-eyrie-78321
 ▸    Confirmation did not match polar-eyrie-78321. Aborted.
jack@jack-virtual-machine:~/Desktop/rails_7_heroku_demo$ heroku addons:destroy heroku-postgresql  --confirm polar-eyrie-78321
Destroying postgresql-pointy-25045 on ⬢ polar-eyrie-78321... done
jack@jack-virtual-machine:~/Desktop/rails_7_heroku_demo$


heroku apps:destroy

 heroku apps:destroy
 ▸    WARNING: This will delete ⬢ polar-eyrie-78321 including all add-ons.
 ▸    To proceed, type polar-eyrie-78321 or re-run this command with
 ▸    --confirm polar-eyrie-78321

>
>  polar-eyrie-78321
Destroying ⬢ polar-eyrie-78321 (including all add-ons)... done

```


rails db:system:change --to=postgresql

## 如何申请和注册一个Heroku
>[油管参考]()

**写在前面**
经测试Heroku的注册屏蔽了某些域名邮箱的注册，比如国内的qq邮箱，国外的有gmail。所以以前长长的注册手段不再适用，跟着下面的思路进行注册。


1. 进入 [Heroku 官网](https://www.heroku.com) 准备开始注册.
2. 因为某些域名的邮箱被限制了注册，所以我们在网上找一些临时邮箱去进行Heroku的注册（Heroku注册成功后可以用更改注册时的用户邮箱）。google 一下 temp mail 每个网站的临时邮箱都试一下，直到找到可以注册的临时邮箱为止。
3. 注册完后采用推荐的方式进行手机auth的绑定.
4. 经测试outlook邮箱现在还能进行绑定，我们注册一个新的outlook邮箱，然后把heroku之前注册的邮箱替换下来。然后再outlook的邮箱中点击链接确认修改，至此所有注册流程已经完成了。后面将介绍如何采用heroku部署一个rails blog。


## 本地使用 快速使用和安装一个postgres数据库
new postrgres docker
```
docker network create app
docker run --name postgres -e POSTGRES_PASSWORD=123123 -e POSTGRES_USER=postgres --network app -p 5432:5432 -v /home/jack/postgres_db:/var/lib/postgresql/data -d postgres

# other
docker run --name postgres -e POSTGRES_PASSWORD=123123 -e POSTGRES_USER=postgres -p 5432:5432 -v /home/jack/postgres_db:/var/lib/postgresql/data -d postgres
docker run --rm --network app postgres psql -h postgres -U postgres

# rails development db url
url: postgres://postgres:123123@127.0.0.1:5432/rails_7_heroku_demo_development
```

version
```
rvm 1.29.12
ruby 3.2.1
rails 7.1.2
docker 24.0.5
docker-compose 2.23.3
postgresql postgres (PostgreSQL) 16.1 (Debian 16.1-1.pgdg120+1)
heroku/8.7.1 linux-x64 node-v16.19.0
```

## 安装Heroku
>[官方安装文档](https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli)
```
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh

heroku --version
```


## 快速构架一个rails应用 采用postgresql数据库
**创建一个rails项目**
```bash
rails new rails_7_heroku_demo --database postgresql

cd rails_7_heroku_demo
# 新的Ubuntu在执行上面命令的时候可能会提示bundle失败 不需要着急，有几个原因，一个是postgres的以来没有安装，仔细看bundle的日志 里面有提示，找到对应的命令执行一下就好，执行完后再进行bundle

bundle install
```

**修改数据库配置文件**











