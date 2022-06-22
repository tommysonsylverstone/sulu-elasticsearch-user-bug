### Steps

1 - initialize new project `composer composer create-project sulu/skeleton my-project -n`
2 - add translation `bin/console sulu:admin:download-language`
3 - create database and initialize `bin/adminconsole sulu:build dev`
4 - download the elasticsearch version that matches your installation's (7.17 in my case) `composer require "elasticsearch/elasticsearch:7.17.*"`
5 - download the article bundle (latest) `composer require sulu/article-bundle`
